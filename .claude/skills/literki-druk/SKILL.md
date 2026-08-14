---
name: literki-druk
description: Buduje wersję do druku (PDF/DOCX) bajek o literkach. Domyślnie PDF najnowszej części. Parametry typ (pdf/docx/oba) i czesc (N/calosc/wszystko) sterują wynikiem. PDF powstaje CZYSTO w Pythonie (reportlab) — bez MS Word i bez drukarki; ma klikalny spis treści, zakładki (część→scenka) i WYRÓŻNIONE ramki z hasłami dla dziecka. Użyj, gdy użytkownik prosi o "wersję do druku", "pdf", "docx", "plik do wydruku części N".
---

# literki-druk — wersja do druku (PDF/DOCX)

Składasz bajki z `opowiadania/czesc-NN - <podtytuł>.md` (jeden plik = jedna część) do pliku do druku. Silnik: [`build_pdf.py`](build_pdf.py).

> **NIGDY nie używaj MS Word do konwersji.** Word przy starcie odpytuje domyślną drukarkę (budzi ją). PDF robimy **czysto w Pythonie (reportlab)** — bez Worda, bez drukarki. **Nie zmieniaj** silnika na ścieżkę przez Worda/`docx2pdf`.

## Hasła dla dziecka w druku (WAŻNE)
- W źródle hasła są oznaczone emoji **👉** (`👉 **KOT MA SOK**`). Emoji to **znacznik formatu**, nie treść.
- W PDF/DOCX skrypt renderuje każde hasło jako **wyśrodkowaną, wyróżnioną ramkę** (żółte tło, granatowy tekst) — dziecko od razu widzi, co ma przeczytać. **Emoji 👉 jest usuwane** (czcionki druku nie mają jego glifu).

## Tytuły i myślniki (WAŻNE)
- Seria: **„Bajki o literkach - czytamy razem"**. Całość: **„Literkowa Kraina. Wszystkie przygody z literami"**.
- W nazwie książki i nazwach części używaj łącznika **„-", NIGDY półpauzy „—"**. Stałe tytułów (`SERIES_TITLE`, `BOOK_TITLE`, `BOOK_BLURB`) są na górze `build_pdf.py`.

## Jak uruchomić

```bash
# DOMYŚLNIE: PDF najnowszej (najwyższej numerem) części
python ".claude/skills/literki-druk/build_pdf.py"

# konkretna część (PDF)
python ".claude/skills/literki-druk/build_pdf.py" --czesc 5

# całość jako jeden PDF (wszystkie części po kolei)
python ".claude/skills/literki-druk/build_pdf.py" --czesc calosc

# wszystko: każda część osobno + całość
python ".claude/skills/literki-druk/build_pdf.py" --czesc wszystko

# format: pdf (domyślnie) | docx | oba
python ".claude/skills/literki-druk/build_pdf.py" --czesc 3 --typ oba
```

- **`--typ`**: `pdf` (domyślnie) · `docx` · `oba`.
- **`--czesc`**: `N` · `calosc` · `wszystko`. Brak = **najnowsza część**.
- Pliki lądują w `druk/` (na żądanie, nieśledzone w repo — patrz `.gitignore`).
- Wymaga `python-docx` (DOCX) i `reportlab` (PDF): `python -m pip install python-docx reportlab`.

## Co dostajesz w PDF (reportlab)
- **Klikalny spis treści** (skacze do części) z numerami stron.
- **Zakładki/outline po lewej: Część → Scenka** (nagłówek `###`) — klikalne.
- **Hasła dla dziecka jako wyróżnione ramki** (żółte tło), wyśrodkowane, dużą czcionką.
- Duża czcionka dla 6-latka: tekst **16 pt** (justowany, interlinia 1,5), część 26, scenka 18, hasło 20; każda część od nowej strony (zajmuje ponad 1,5 strony); numeracja stron.
- **Czcionka Arial** (z `C:\Windows\Fonts` albo `fonts/` w repo; polskie znaki OK). Gdy brak TTF Ariala — Helvetica.

## DOCX (opcjonalnie, `--typ docx`/`oba`)
- python-docx; nagłówki jako style Word (Heading 1 = Część, 2 = Scenka) → panel nawigacji w Wordzie.
- Wstawione **pole spisu treści** (klikalne po aktualizacji: Ctrl+A, potem F9).
- Hasła jako wyśrodkowane, cieniowane (żółte) akapity.
- **Generowanie DOCX nie uruchamia Worda** (to zwykły plik). Jeśli użytkownik sam otworzy DOCX w Wordzie — to jego decyzja.

## WAŻNE przy druku
1. **Do drukarni: PDF** (nie DOCX). PDF ma zaszytą czcionkę i strukturę.
2. **Czcionka**: Arial (zaszyty w PDF); gdy brak TTF Ariala — Helvetica.
3. **Oprawa / A5**: obecnie A4 z marginesem na oprawę (lewy 2,5 cm). Dla książeczki dla dzieci częściej A5 — do zmiany w stałych na górze skryptu.
4. **Korekta** wszystkich części (`literki-fix wszystkie`) przed drukiem.
5. **Ilustracje / strona redakcyjna (autor, rok, ISBN)** — dołóż, jeśli to publikacja.

## Rozbudowa
Parametry (czcionka, rozmiary, marginesy, tytuły, kolory ramki hasła) to stałe/styl na górze `build_pdf.py`.
