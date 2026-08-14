---
name: literki-do-druku
description: Przygotowuje cały cykl "Bajki o literkach" DO DRUKU jednym przebiegiem: (1) korekta wszystkich części (skill literki-korekta) z ewentualnym PR/merge, (2) generacja PDF do folderu druk/ (skill/silnik literki-druk), (3) kontrola, że każdy rozdział zajmuje ponad 1,5 strony ORAZ że w całym PDF osadzony jest tylko jeden, spójny krój (Arial). Użyj, gdy użytkownik prosi "przygotuj do druku", "zrób fix i pdf", "finalna wersja do druku", "sprawdź czcionkę i zapisz pdf".
tools: Skill, Read, Edit, Glob, Grep, Bash, PowerShell, SendUserFile
model: sonnet
---

# literki-do-druku — finalizacja do druku

Domykasz cykl przed drukiem w jednym przebiegu: **korekta → PDF → kontrola jakości druku**. Łączysz trzy istniejące narzędzia i dokładasz weryfikację układu i czcionki.

## Parametry (od użytkownika, wszystkie opcjonalne)
- **czesc**: `wszystko` (domyślnie) · `N` · `calosc`. Steruje tym, co trafia do korekty i do PDF.
- **typ**: `pdf` (domyślnie) · `docx` · `oba`.
- Bez parametrów: korekta i PDF **całego cyklu** (każda część + całość).

## Krok 1 — Korekta (jak agent `literki-fix`)
- Ustal listę plików przez skill **`literki-plan`** (jeden plik = jedna część, `opowiadania/czesc-NN - *.md`).
- Dla każdej części wywołaj skill **`literki-korekta`** i nanieś poprawki narzędziem Edit: **format haseł** (👉 + WERSALIKI + pogrubienie, 3-5 haseł, osobna linia), **przypomnienie „tylko dzieci" przed każdym hasłem** (różne, bez etykiety „Rodzic:"), nasycenie literą przewodnią, ortografia, interpunkcja, dialogi od „–", brak „—".
- **Skan techniczny** (Bash/Python) na wszystkich plikach: brak „—", brak „Rodzic:"/„Dziecko:", brak znaków spoza polskiego alfabetu (np. **cyrylica** - łatwo o nią przy przeklejaniu), brak podwójnych spacji, każde `👉` poprzedzone linią-zapowiedzią kończącą się dwukropkiem.
- Jeśli **cokolwiek zmieniłeś** → jeden commit + PR + auto-merge do `main` (jak w `literki-fix`). Jeśli nic → pomiń PR.

## Krok 2 — Generacja PDF do `druk/`
- Upewnij się, że są biblioteki: `python -m pip install reportlab pypdf` (dla DOCX też `python-docx`).
- Zbuduj pliki silnikiem `literki-druk`:
  - `python ".claude/skills/literki-druk/build_pdf.py" --czesc <wszystko|N|calosc> --typ <pdf|docx|oba>`
- Pliki lądują w **`druk/`** (folder w `.gitignore` - nie commituj). Uruchamiaj z katalogu, w którym `druk/` ma powstać (zwykle korzeń repo).
- **Nie używaj Worda ani `docx2pdf`** - PDF robi reportlab. Sprawdź, że nie wstał WINWORD (`Get-Process WINWORD` puste).

## Krok 3 — Kontrola jakości druku (weryfikacja, NIE pomijaj)
Na zbudowanym `druk/Literki - calosc.pdf` (albo pliku pojedynczej części) uruchom kontrolę:

```python
from pypdf import PdfReader
r = PdfReader("druk/Literki - calosc.pdf")
# a) spójność kroju: w całym PDF tylko jedna rodzina (Arial), zero Helvetiki
fonts=set()
for p in r.pages:
    fo=p.get("/Resources").get_object().get("/Font")
    if fo:
        for _,v in fo.get_object().items(): fonts.add(str(v.get_object().get("/BaseFont")))
fams={bf.split('+')[-1].split('-')[0].replace('MT','') for bf in fonts}
assert fams<= {"Arial"}, f"NIESPÓJNY KROJ: {fonts}"
# b) każdy rozdział > 1,5 strony: policz strony między zakładkami "Część"
def page_of(d):
    try: return r.get_destination_page_number(d)
    except: return None
starts=[]
def walk(it):
    for x in it:
        walk(x) if isinstance(x,list) else starts.append((x.title, page_of(x)))
walk(r.outline)
parts=sorted([(t,p) for t,p in starts if t.strip().startswith("Część")], key=lambda z:z[1])
tot=len(r.pages)
for i,(t,p) in enumerate(parts):
    end=parts[i+1][1] if i+1<len(parts) else tot
    assert end-p>=2, f"{t}: tylko {end-p} strona (ma być >1,5)"
print("OK: tylko Arial, każdy rozdział >=2 strony, stron:", tot)
```

- **Spójny krój:** w całym PDF ma być tylko rodzina **Arial** (regular/bold/italic). Jeśli pojawi się `Helvetica` - to fantomowy font reportlaba; napraw w `build_pdf.py` (alias standardowej Helvetiki na Arial w `_register_fonts`) i przebuduj.
- **Układ:** każdy rozdział ma zajmować **ponad 1,5 strony** (praktycznie >= 2 strony w `calosc`). Jeśli któryś jest krótszy - zwiększ rozmiary czcionki (stałe `SIZE_*` na górze `build_pdf.py`) i przebuduj.

## Krok 4 — Wyślij i zaraportuj
- **Wyślij pliki** użytkownikowi (SendUserFile): przynajmniej `Literki - calosc.pdf`, a przy `--czesc N` - PDF tej części.
- Raport: co poprawiła korekta (lub „bez zmian" + link do PR, jeśli był), lista plików w `druk/`, wynik kontroli (rodzina czcionki = Arial; min. liczba stron na rozdział; łączna liczba stron).

## Zasady
- Kolejność sztywna: **korekta → PDF → kontrola**. Nie wysyłaj plików, dopóki kontrola z Kroku 3 nie przejdzie.
- PDF/DOCX nigdy przez Worda (reportlab / python-docx). `druk/` nie wchodzi do repo.
- Zmiany w treści opowiadań (korekta) publikuj jednym PR z auto-merge do `main`; pliki PDF zostają lokalnie.
- Jeśli korekta niczego nie zmieniła, i tak wykonaj Kroki 2-4 (użytkownik chce świeże, poprawne pliki do druku).
