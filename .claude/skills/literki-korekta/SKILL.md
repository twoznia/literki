---
name: literki-korekta
description: Sprawdza i POPRAWIA gotową bajkę o literkach — poprawność językową (ortografia, literówki, interpunkcja), zapis dialogów, ORAZ rzeczy specyficzne dla tej serii: czy hasła dla dziecika są dobrze sformatowane (👉 + WERSALIKI + pogrubienie, osobna linia), czy zawierają litery przewodnie danej części i czy słowa w hasłach są odpowiednie dla 6-latka. Nie zmienia fabuły. Użyj, gdy użytkownik prosi "sprawdź/popraw bajkę o literkach", "korekta", "literówki" albo /literki-korekta. Do sprawdzenia części po numerze użyj agenta literki-fix.
---

# Literki — korekta i poprawa tekstu

Sprawdzasz gotową bajkę z cyklu „Bajki o literkach" pod kątem **poprawności językowej, poprawnego formatu haseł i wartości edukacyjnej**, a następnie **nanosisz poprawki** (narzędziem Edit). Poprawiasz — **nie przepisujesz fabuły** ani nie zmieniasz stylu i humoru.

## Jak działać

1. **Wczytaj** wskazany plik (Read). Jeśli nie podano — zapytaj który albo weź plik, o którym mowa w rozmowie.
2. **Ustal literę/litery przewodnie** tej części ze skilla [`literki-plan`](../literki-plan/SKILL.md) (numer części → litery). To potrzebne do sprawdzenia haseł.
3. **Przejrzyj** tekst według listy kontrolnej i wypisz usterki (krótko: cytat → propozycja).
4. **Popraw** każdą usterkę przez Edit (dokładne dopasowanie fragmentu, przy powtarzalnym błędzie `replace_all`).
5. **Raport**: zmiany (było → jest) pogrupowane wg kategorii. Jeśli nic nie wymaga poprawy — napisz to wprost.

## Lista kontrolna

### 1. Format haseł dla dziecka (NAJWAŻNIEJSZE dla tej serii)
Każde hasło, które ma przeczytać dziecko, MUSI być:
- w **osobnej linii**,
- poprzedzone emoji **👉**,
- pisane **DUŻYMI LITERAMI** (WERSALIKI),
- **pogrubione** (`**...**`).
Wzór: `👉 **KOT MA SOK**`. Popraw hasła, którym brakuje 👉, pogrubienia albo są małymi literami. Sprawdź, czy przed hasłem jest linia rodzica (`*Rodzic:*` + wprowadzenie), a po nim narracja z widocznym **skutkiem** odczytania (coś się dzieje). Jeśli skutku brak — zgłoś (hasło ma „otwierać bramkę").

### 2. Litery przewodnie w hasłach (wartość edukacyjna)
- Sprawdź, że hasła są **nasycone literą/literami przewodnimi** danej części (zwłaszcza literą „Skupienia"). Jeśli hasło prawie nie zawiera ćwiczonej litery — **zgłoś** i zaproponuj mocniejszy wariant (nie zmieniaj sam sensu sceny bez potrzeby).
- Policz hasła: powinno ich być **3-5**. Za mało / za dużo — zgłoś.
- **Słowa w hasłach** mają być znane 6-latkowi i łatwe do zliterowania (krótkie, proste sylaby na łatwym poziomie). Wyłap słowa za trudne, wieloznaczne albo z mylącą ortografią (chyba że to celowo ćwiczona różnica, np. Ó vs O w części 9).

### 3. Ortografia i literówki
- Typowe pułapki: **ó/u, rz/ż, ch/h, ą/ę, ś/sz, ci/ć, ń/ni**. Uwaga zwłaszcza w częściach, które właśnie te litery ćwiczą — tekst rodzica ma być wzorowo poprawny.
- Zbitki i przestawione litery, podwojone/zgubione litery, sklejone wyrazy.
- Wielkie litery na początku zdań i w nazwach własnych (nazwy krain, imiona liter-bohaterów).
- **Litery-bohaterowie** zapisywane wielką literą, gdy występują jako postać (np. „**A** zaśpiewała", „siostry **A** i **O**"). W obrębie hasła wszystko wielkimi — to celowe.

### 4. Interpunkcja i zapis dialogów
- Dialogi (kwestie liter-bohaterów): półpauza **–** (U+2013) na początku, spacja, kursywa: `– *tekst*`. **Kwestia zaczynająca się od zwykłego „-" → popraw na „–"** (inaczej Markdown zrobi bullety). Atrybucja po kwestii też „–".
- Zdania pytające/wykrzyknikowe z `?`/`!`; wielokropek `...`; brak podwójnych spacji.
- Cudzysłowy polskie „…" przy cytatach/napisach (poza hasłami, które mają swój format).

### 5. Rodzaj gramatyczny liter-bohaterów
- „Litera" jest rodzaju żeńskiego, ale **każda litera-postać ma swój charakter**; trzymaj się tego, jak wprowadzono postać w danej bajce (np. „siostra **A**" → żeński; „**brat Ż**", „budowniczy **B**" → męski). Sprawdź, czy czasowniki i przymiotniki zgadzają się z przyjętym rodzajem postaci **konsekwentnie w całej bajce** (nie raz „A zaśpiewał", raz „A zaśpiewała").
- Sprawdź zaimki i końcówki (ten/ta, sam/sama, mały/mała).

### 6. Składnia i naturalność
- **Orzecznik po „być" w NARZĘDNIKU**: „jestem literą", „będę słowem" (nie „jestem litera").
- Wyłapuj konstrukcje nienaturalne/kalki — czytaj każde zdanie „na głos w głowie". Nie ruszaj celowych żartów, zawołań i efektów dźwiękowych.
- Zdania krótkie i proste — jeśli któreś jest za długie/zawiłe dla 6-latka, zaproponuj rozbicie (ale nie przepisuj całości).

### 7. Struktura i styl (lekko)
- Tytuł `# Część NN - …` (numer części + podtytuł, separator `-`). Nagłówki scenek to **sam pogrubiony tytuł, bez „Rozdział 1/2/3:"** — jeśli jest taki prefiks, usuń.
- **Długi myślnik „—" (em dash) → „-"** w narracji i tytułach. (Półpauzę „–" na początku kwestii dialogowej zostaw.)
- Długość warstwy fabularnej (rodzic) ok. **200-300 słów** — jeśli mocno odbiega, zgłoś (nie tnij sam bez potrzeby).
- **Nie poprawiaj** celowych efektów dźwiękowych (*Bęc!, Chlust!, Wziuuu!, KLIK!*), kolokwializmów i żartów.
- Ton ciepły i bezpieczny; brak treści straszących 6-latka.

## Zasady
- **Popraw, nie przepisuj.** Zmieniasz błędy językowe, format haseł i niespójności, nie fabułę ani humor.
- Przy wątpliwości „błąd czy zamierzony żart / celowa trudna litera" — zostaw, ale **wypisz w raporcie** jako pytanie do decyzji użytkownika.
- Po skończeniu podaj zwięzły raport (było → jest). **Nie commituj ani nie pushuj** — to nie jest zadanie tego skilla (robi to agent `literki-fix`/`literki-fabryka`).
