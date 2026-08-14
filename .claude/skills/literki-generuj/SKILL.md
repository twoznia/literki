---
name: literki-generuj
description: Generuje interaktywną, absurdalnie zabawną bajkę edukacyjną o literkach dla 6-latka, do czytania NAPRZEMIENNEGO (rodzic czyta fabułę, dziecko czyta "magiczne hasła/zaklęcia" z literami przewodnimi). Użyj, gdy użytkownik prosi o "bajkę o literkach", "kolejną część", "część N o literach", podaje numer części (1-20) albo pisze /literki-generuj. Cykl ma 20 części opisanych w info/idea.md — każda uczy innej litery lub grupy liter.
---

# Literki — generator interaktywnej bajki o literach

Piszesz kolejną część cyklu bajek edukacyjnych o **literkach** dla **6-letniego dziecka**, które zna już wszystkie litery, ale dopiero uczy się czytać (literuje pojedyncze słowa). Bajka jest **interaktywna, do czytania naprzemiennego**: rodzic czyta płynnie główną fabułę, a dziecko czyta **magiczne hasła / zaklęcia / tabliczki**, bez których akcja nie ruszy dalej. Historia ma śmieszyć i angażować 6-latka (absurdalny humor, szalone zwroty akcji, zwariowane postaci) — a przy okazji ćwiczyć literę lub litery przewodnie z danej części.

Pełny plan 20 części i zasady bazowe są w [`info/idea.md`](../../info/idea.md) — traktuj ten plik jako źródło prawdy o tym, która część uczy jakich liter.

## TWARDE ZASADY (ustalone — zawsze przestrzegaj)

- **Numer części (1-20)** wybiera litery przewodnie — patrz „PLAN CYKLU" w [`info/idea.md`](../../info/idea.md). Nie zmieniaj przypisania liter do części.
- **Mechanika naprzemienna:** w każdej bajce **od 3 do 5 haseł dla dziecka**. Hasło jest bramką: dopóki dziecko go nie przeczyta, akcja stoi. Po odczytaniu — dzieje się coś zabawnego (kłódka wystrzeliwuje, most się pojawia, potwór zamienia się w kotka).
- **Hasła MUSZĄ zawierać jak najwięcej słów z literą/literami przewodnimi** danej części (patrz „Jak budować hasła"). To sedno ćwiczenia — nie hasła „ozdobne", tylko celowe pod literę.
- **Formatowanie hasła (sztywne):** KAŻDE hasło w OSOBNEJ LINII, poprzedzone emoji 👉, pisane **DUŻYMI LITERAMI i POGRUBIONE**. Przed hasłem krótka linia rodzica („*Rodzic:*" + wprowadzenie), która daje kontekst („odczytał napis", „na tabliczce widniało").
- **Tekst rodzica** to zwykły akapit prozą (płynna fabuła). **Tekst dziecka** to tylko hasła — nigdy nie wrzucaj dziecku długiego zdania do przeczytania.
- **Poziom trudności** dobierany do numeru: na początku (część 1-5) ŁATWY — hasła krótkie, 2-3 słowa, proste sylaby (KOT MA SOK). Dalej (część 6-14) TRUDNIEJSZY — dłuższe słowa, więcej liter przewodnich. Finałowe (15-20) — najtrudniejsze, dłuższe hasła, zbitki. Użytkownik może nadpisać poziom.
- **Myślniki:** w narracji i tytułach TYLKO łącznik „-" (NIGDY em dash „—"). **Dialogi ZAWSZE od półpauzy „–"** (`– *kwestia*`), nigdy od „-" (Markdown zrobiłby bullety); atrybucja po kwestii też „–".
- **Bezpiecznie i ciepło** — żadnej prawdziwej krzywdy, przemocy ani strachu nie do udźwignięcia dla 6-latka. Wpadki są groźne „na niby" i kończą się śmiechem.
- **Poprawna, prosta polszczyzna** — krótkie zdania, słowa znane 6-latkowi. Litery i dwuznaki zapisuj tak, jak dziecko je zna.

## Zanim zaczniesz

1. Ustal **numer części** (1-20). Jeśli użytkownik podał — użyj go. Jeśli nie — zapytaj albo weź kolejną, której jeszcze nie ma w `opowiadania/`.
2. Z [`info/idea.md`](../../info/idea.md) odczytaj **litery przewodnie** tej części i jej motyw (np. „Część 1: A i O — Śpiewające siostry i aparatowe awarie").
3. Ustal **poziom trudności** (domyślnie wg numeru — patrz wyżej; użytkownik może nadpisać).
4. Wymyśl **świeży motyw/miejsce akcji** pasujące do liter (kraina, wyprawa, zamek, warsztat) — takie, którego jeszcze nie było w innych częściach.
5. Zaplanuj **3-5 punktów, w których akcja się zatrzymuje** i potrzebuje hasła od dziecka. To one wyznaczają rytm bajki.

## Sztywny szkielet (trzymaj się kolejności)

1. **Otwarcie.** Wprowadź krainę/świat literek i **postaci-litery** z tej części (litery przewodnie jako bohaterowie — patrz „Litery jako postaci"). Zabawny obrazek świata, jeden żart „dla dorosłego" mrugnięciem.
2. **Zawiązanie akcji.** Coś się psuje / gubi / zaczaruje — pojawia się cel wyprawy albo problem do rozwiązania. Napięcie „na niby", pełne humoru.
3. **Pierwsza bramka — HASŁO 1.** Bohater natrafia na przeszkodę (kłódka, brama, śpiąca litera, zaczarowany most). Rodzic czyta wprowadzenie, **dziecko czyta hasło**, akcja rusza z hukiem/efektem dźwiękowym.
4. **Rozwinięcie + kolejne bramki (HASŁO 2, 3…).** Wyprawa toczy się dalej, co jakiś czas kolejna zabawna przeszkoda otwierana hasłem. Każde hasło mocniej „dosypuje" litery przewodniej. Zwroty akcji, dziwne postaci, absurd rośnie.
5. **Kulminacja — HASŁO finałowe.** Najważniejsze, często najdłuższe/najtrudniejsze hasło ratuje sytuację (budzi wielką literę, otwiera skarbiec, rozwiewa czar).
6. **Rozwiązanie + ciepły morał.** Problem rozwiązany, litery świętują, krótki pozytywny morał (np. „razem litery tworzą słowa", „warto próbować czytać").
7. **Zakończenie.** Jedno-dwa zdania domykające krainę literek + delikatna zapowiedź kolejnej litery/części. Ciepło, bez nachalnego dydaktyzmu.

## Litery jako postaci

Główni bohaterowie to **litery przewodnie danej części** — ożywione, z charakterem wynikającym z ich kształtu, dźwięku i „osobowości" z planu w [`info/idea.md`](../../info/idea.md). Kilka wskazówek:

- **Charakter z kształtu i dźwięku:** A śpiewa („aaa!"), S syczy jak wąż, Ł nosi kapelusz z daszkiem (kreska), Ó ma kreskę-antenkę, litery z ogonkami (Ą, Ę) machają nimi jak pędzelkami, Ż i Ź to bracia „z kropką" i „z kreską", M to dwa wzgórza, N jedno, R warczy, J skacze jak haczyk na rybę, Ń chowa się nieśmiało za innymi.
- **Trzymaj się opisów z `idea.md`** — każda część ma tam gotowy „haczyk" charakterologiczny (np. część 5: „Prosta L i Ł w kapeluszu z daszkiem").
- **Litery mają relacje** — siostry, bracia, bliźniacy, rywale, para przyjaciół. To napędza fabułę i humor.
- **Absurdalne zawody i sytuacje** dla liter: litera-listonosz, litera-strażak, śpiewaczka, budowniczy, aptekarz. Im dziwniej, tym lepiej dla 6-latka.
- W częściach zbiorczych (18, 19, 20) litery spotykają się grupami — festiwal, zjazd, budowa królestwa. Zadbaj, by każda litera przewodnia dostała swój moment.

## Jak budować hasła dla dziecka

Hasło to serce ćwiczenia. Zasady:

- **Nasyć literą przewodnią.** W haśle ma być **jak najwięcej słów zawierających literę/litery** z danej części. Przykład dla części 1 (A, O): `👉 **KOT MA SOK**` (K**O**T, MA, S**O**K) — ale celuj w jeszcze więcej trafień, np. `👉 **OKO MA OSA**`, `👉 **LATA SOWA**`.
- **Dobierz długość do poziomu:**
  - ŁATWY (cz. 1-5): 2-3 krótkie słowa, proste sylaby otwarte (KOT MA SOK, OKO LALA).
  - TRUDNIEJSZY (cz. 6-14): 3-4 słowa, dłuższe, z dwuznakami/miękkościami przewodnimi (CICHY KOŃ ŚPI, ŻABA MA ŻÓŁW).
  - NAJTRUDNIEJSZY (cz. 15-20): dłuższe hasła, więcej słów, celowe zbitki liter przewodnich.
- **Tylko słowa znane 6-latkowi** i łatwe do zliterowania. Bez abstraktów, bez trudnej ortografii, która myli (chyba że to właśnie ćwiczona różnica, np. Ó vs O w cz. 9, U vs Ó — wtedy z rozmysłem).
- **Hasło ma „coś robić" w fabule** — to zaklęcie/rozkaz/nazwa/napis na tabliczce. Po jego odczytaniu następuje konkretny, zabawny skutek.
- **3-5 haseł na bajkę.** Rozłóż je równomiernie (nie wszystkie na początku). Ostatnie zwykle najważniejsze.
- **Nie powtarzaj tego samego hasła** w obrębie bajki ani (najlepiej) między częściami.

## Formatowanie (sztywne — tak jak w `info/idea.md`)

- **Tekst dla rodzica:** zwykły akapit prozą, ok. **200-300 słów** łącznie w całej bajce dla warstwy fabularnej (rozłożony między hasłami). Pełne zdania, płynna narracja.
- **Tekst dla dziecka:** **KAŻDE HASŁO W OSOBNEJ LINII**, poprzedzone emoji **👉**, pisane **DUŻYMI LITERAMI i POGRUBIONE**.
- **Oznaczaj role** kursywą na początku linii wprowadzającej: `*Rodzic:*` przed narracją prowadzącą do hasła. Samo hasło jest w osobnej linii (dziecko od razu widzi, co czyta).
- **Wzór (z `idea.md`):**

  > *Rodzic:* Pan Bóbr popatrzył na tajemniczą kłódkę i odczytał napis:
  >
  > 👉 **KOT MA SOK**
  >
  > *Rodzic:* Kłódka natychmiast wystrzeliła w powietrze...

- **Myślniki:** narracja/tytuły — łącznik „-" (nigdy „—"). Dialogi — półpauza „–" na początku kwestii: `– *Aaa, znów awaria aparatu!*`. Nigdy nie zaczynaj kwestii od „-".
- **Markdown jak w repo:** `#` z tytułem części, `###` zabawne nagłówki scenek (sam pogrubiony tytuł, bez „Rozdział 1/2/3:"), imiona/litery-bohaterów można pogrubić przy pierwszym pojawieniu.
- **Tytuł (H1):** krótki, zabawny, z numerem części i motywem, np. `# Część 1 - Śpiewające siostry A i O`.

## Styl i humor

- **Absurdalny humor** — szalone zwroty akcji, dziwne sytuacje, zwariowane postaci. Historia MA śmieszyć 6-latka.
- **Dwa piętra humoru:** dla dziecka — efekty dźwiękowe (**Bęc! Chlust! Pyk! Wziuuu! KLIK!**), „brzuszkowy" humor, przesada, powtórzenia, zabawne wpadki liter; dla dorosłego czytającego — drobne mrugnięcia (biurokracja alfabetu, „litery na urlopie", ironiczne porównania) — z umiarem, nigdy kosztem zrozumiałości dla dziecka.
- **Proste słowa, krótkie zdania**, narrator gada do dziecka: *„No i słuchajcie…", „A wiecie, co było dalej?"*.
- **Napięcie zawsze „na niby"** i rozwiązywane sprytem/współpracą liter. Ciepło i bezpiecznie.
- **Powtarzalne sygnatury** (dźwięki liter, powracające gagi) budują rozpoznawalność cyklu — ale nie kopiuj tych samych zdań między częściami.

## Długość i format pliku

- **Warstwa fabularna (rodzic): ok. 200-300 słów.** Całość bajki z hasłami i nagłówkami może być nieco dłuższa, ale nie przytłaczaj — to bajka do jednego czytania.
- **3-5 haseł dla dziecka**, każde nasycone literą przewodnią, we właściwym formacie (👉 + WERSALIKI + pogrubienie, osobna linia).
- **Umiejscowienie i numeracja** wynikają ze skilla [`literki-plan`](../literki-plan/SKILL.md): **jeden plik = jedna część**, `opowiadania/czesc-NN - <podtytuł>.md` (numer części dwucyfrowo z zerem). Zapytaj `literki-plan`, którą część piszesz, jakie ma litery przewodnie i jaki poziom.
- **Tytuł (H1):** `# Część NN - <podtytuł>` (numer części + zabawny podtytuł; separator to zwykły łącznik `-`).

## Checklista przed oddaniem (odhacz w głowie)

- [ ] Wybrana **właściwa część (1-20)** i jej **litery przewodnie** wg `info/idea.md`.
- [ ] **Litery przewodnie występują jako postaci** z charakterem z planu.
- [ ] **3-5 haseł** dla dziecka, każde w osobnej linii, z **👉**, WERSALIKAMI i **pogrubieniem**.
- [ ] Każde hasło **nasycone literą/literami przewodnimi** i dobrane długością do poziomu trudności.
- [ ] Każde hasło **coś uruchamia** w fabule (jest bramką, po której akcja rusza).
- [ ] Tekst rodzica ok. **200-300 słów**, płynna proza; tekst dziecka to tylko hasła.
- [ ] **Absurdalny humor**, efekty dźwiękowe, zwroty akcji — śmieszy 6-latka.
- [ ] Brak długiego myślnika „—" (tylko „-"); dialogi od półpauzy „–".
- [ ] Prosta polszczyzna, słowa znane 6-latkowi, bezpiecznie i ciepło.
- [ ] Ciepły, prosty morał i delikatna zapowiedź kolejnej litery/części.
