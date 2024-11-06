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

Stjärna ovanför _( * )_ betyder att vi hämtar **allt** från tabellen, alla kolumner/attribut och alla rader från den specifika tabellen _( table )_.

Om vi inte är intresserade utav alla information i tabellen så kan vi modifiera denna query en aning för att ge oss ett lite mer specifikt resultat. För att göra det så ersätter vi stjärnan _( * )_ med ett eller flera kolumnnamn. De olika kolumnnamnet måste separeras med ett komma.

```sql
SELECT first_name, last_name FROM students
```

[Till toppen](#2024-11-06-intro-sql)

#### FROM

[Till toppen](#2024-11-06-intro-sql)

### Filtrera med WHERE

[Till toppen](#2024-11-06-intro-sql)

#### AND

[Till toppen](#2024-11-06-intro-sql)

#### OR

[Till toppen](#2024-11-06-intro-sql)

### Sortera med ORDER BY

[Till toppen](#2024-11-06-intro-sql)

### Begränsa antal med LIMIT

[Till toppen](#2024-11-06-intro-sql)

### Möstermatchning med LIKE

[Till toppen](#2024-11-06-intro-sql)

#### IN

[Till toppen](#2024-11-06-intro-sql)

#### BETWEEEN

[Till toppen](#2024-11-06-intro-sql)
