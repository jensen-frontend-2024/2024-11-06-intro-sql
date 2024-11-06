# 2024-11-06 Intro SQL

<details open>
    <summary>Innehåll</summary>

- [Skapa en database](#skapa-en-database)
  - [Fylla på med mockad data](#fylla-på-med-mockad-data)
- [Grunderna i SQL](#grunderna-i-sql)
  - [Nyckelord](#nyckelord)
  - [Hämta med hjälp av SELECT](#hämta-med-hjälp-av-select)
    - [FROM](#from)
  - [Filtrera med WHERE](#filtrera-med-where)
    - [AND](#and)
    - [OR](#or)
  - [Sortera med ORDER BY](#sortera-med-order-by)
  - [Begränsa antal med LIMIT](#begränsa-antal-med-limit)
  - [Möstermatchning med LIKE](#möstermatchning-med-like)
    - [IN](#in)
    - [BETWEEN](#betweeen)
    </details>

## Skapa en database

### Fylla på med mockad data

Vi avänder oss utav en hemsida för att ta farm testdata, även kallad mockdata.

[mockaroo.com](https://mockaroo.com/)

Väldigt enkel att använda, du kan specisera exakt vilka olika typeer av data du behöver plus att du kan få det i SQL-format. Alltså en query som du kan köra i ditt SQLite för att inserta all data.

[Till toppen](#2024-11-06-intro-sql)

## Grunderna i SQL

SQL står Stuctured Query Language och är ett språk som vi använder för att kommunicera med relationsdatabaser som använder sig av SQL. Så i detta språk så ställer vi frågor till databasen, och dessa fråga kan inkludera data som vi önksar att se, data vi önskar att uppdatera, lägga till och även ta bort.

[Till toppen](#2024-11-06-intro-sql)

### Nyckelord

Ett nyckelord är en term/ord som är reserverat i SQL och kan alltså inte avnändas till något annan än det de är till för. Exempel på dessa är:

```sql
SELECT
WHERE
FROM
AND
OR
JOIN
LIKE
GROUP BY
-- plus många fler...
```

Som ni ser ovan så är de i stora bokstäver men det är INTE obligatoriskt. Det går lika bra med små bokstäver. Dock så är det best practise att använda stora bokstäver på alla nyckelorden i SQL.

Varja nyckelord har ett specifikt syfte. Vi kan använda flera av de i samma SQL-fråga och då kommer varje nyckelord hantera en specifik aspekt av SQL-frågan.

[Till toppen](#2024-11-06-intro-sql)

### Hämta med hjälp av SELECT

`SELECT` används för att hämta saker ur en databas. Så i sin renaste form så ser den ut så här:

```sql
SELECT * FROM table
```

Stjärna ovanför _( \* )_ betyder att vi hämtar **allt** från tabellen, alla kolumner/attribut och alla rader från den specifika tabellen _( table )_.

Om vi inte är intresserade utav alla information i tabellen så kan vi modifiera denna query en aning för att ge oss ett lite mer specifikt resultat. För att göra det så ersätter vi stjärnan _( \* )_ med ett eller flera kolumnnamn. De olika kolumnnamnet måste separeras med ett komma.

```sql
SELECT first_name, last_name FROM students
```

[Till toppen](#2024-11-06-intro-sql)

#### FROM

`FROM` används för att specifisera vilken tabell vi vill hämta våran data ifrån.

[Till toppen](#2024-11-06-intro-sql)

### Filtrera med WHERE

Detta använda när vi vill hämta data utifrån en specifikt villkor. Kan vara ett namn, ålder, id eller egentligen vad som helst bland de existerande kolumnerna. Ett villkor kan vi säga som måste var uppfyllt för att datan ska returneras till oss.

```sql
SELECT * FROM students WHERE first_name = "Niklas"
```

Det här queryn kommer att ge oss ett resultat som innehåller alla studenter vars namn är like med "Niklas", och stavningen är viktigt här. Skriver vi stor vi bokstav någonstans så kommer det att ingå i villkoret.

`WHERE` kräver alltid specifika värden så vi kan inte söka på något som innehåller något, utan det är hela värdet som räknas.

[Till toppen](#2024-11-06-intro-sql)

#### AND

Denna används för att lägga ytterligare villkor i vår WHERE-fråga. Så länge vi använder AND så måste båda, eller om det är flera, villkoren att stämma. Så till exmempel:

```sql
SELECT * FROM students
WHERE first_name = "niklas"
AND last_name = "fähnrich"
```

Detta kommer att returnera alla studenter som uppfyller båda villkoren. Blir också queryn längre så kan det vara fint att radbryta den och då radbryter vi på nyckelorden.

[Till toppen](#2024-11-06-intro-sql)

#### OR

Här måste minst ett av villkoren vara sanna för att den specifika raden ska inkluderas i resultatet.

```sql
SELECT * FROM students
WHERE first_name = "niklas"
OR last_name = "fähnrich"
```

Så detta resultat kommer att inkludera alla studentera med first_name som är niklas eller last_name som är fähnrich.

[Till toppen](#2024-11-06-intro-sql)

### Sortera med ORDER BY

Används för att sortera resultaten efter en specifik kolumn, antingen i stigand eller fallande ordning. Till exempel:

```sql
SELECT * FROM students
ORDER BY email
```

#### ASC

_(ascending)_ - Denna användas tillsammans med ORDER BY och betyder att resultatet sorteras i stigande ordning utifrån den givna kolumnen. Detta är även default-värdet om inget anges.

```sql
SELECT * FROM students
ORDER BY email ASC
```

#### DESC

_(descending)_ - Precis som ovan fans i fallande ordning.

```sql
SELECT * FROM students
ORDER BY email DESC
```

[Till toppen](#2024-11-06-intro-sql)

### Begränsa antal med LIMIT

Så om vi vill begränsa antalet resultat som inkluderas, så kan vi använda LIMIT. Den läggs på sist i SQL-frågan.

```sql
SELECT * FROM students
LIMIT 10
```

[Till toppen](#2024-11-06-intro-sql)

### Möstermatchning med LIKE

LIKE används för att göra breda sökningar där vi inte har specifika värden. Vi kanske har en del av ett värde och vill söka på alla rader vars kolumn består av den delan av värdet. Vi kanske söker efter alla studenter som börjar på bokstave "L", eller alla studenter vars email innehåller ".se" eller något liknande.

Detta kan kallas för att vi söker efter mönster i vår tabell. Mönstret ska skrivas inom citat-tecken och vi kan använda specialtecken för att specicera vår sökning. Tänkt även på att stor eller liten bokstav inte spelar någon roll när vi använder "LIKE". Den är så kallade "case-insensitve".

**%-tecknet används för att wildcard-matchningar, noll eller flera.**

För att ta ett exempel, vi söker efter alla namn som börjar på "k":

```sql
SELECT first_name FROM students
WHERE first_name LIKE "k%"
```

"k%" i det här fallet betyder alla first_name som börjar på "k" och sen ett okänd antal wildcard-tecken efteråt.

%-tecknet kan används före eller efter vårt möster för att söka på värden som antingen börjar på något specifikt eller slutar på något specifikt. Vi kan även ha %-tecken både före och efter om vi vill att vårt värde som vi söker ska innehålla vårat mönster.

Här är ett exemple där vi sökert efter alla first_name som innhåller bokstäverna "ia" efter varandra.

```sql
SELECT * FROM students
WHERE first_name LIKE "%ia%"
```

`_`-tecknet _( underscore )_ används för att matcha specifikt ett okänd tecken. Så om vi söker efter något liknande som det här:

"h_nt"

Denna matcher mot hunt, hint och så vidare. Ett tecken på den andra positionen i mönstret är alltså okängd. Vill vi söka efter ett mönster som innehåller flera okända tecken och vi vet hur många okända tecken det är så kan vi skriva flera understräck efter varandra. 

[Till toppen](#2024-11-06-intro-sql)

#### IN

[Till toppen](#2024-11-06-intro-sql)

#### BETWEEEN

[Till toppen](#2024-11-06-intro-sql)
