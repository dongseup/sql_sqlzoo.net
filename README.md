# SQLZOO

[사이트 바로가기](https://sqlzoo.net/wiki/SELECT_Quiz)

---

### SELECT basic

[학습](https://sqlzoo.net/wiki/SELECT_basics)

```
SELECT population FROM world WHERE name = 'France';
```

```
SELECT name, population FROM world WHERE name IN ('Sweden', 'Russia', 'India', 'China');
```

```
SELECT name, area FROM world WHERE area BETWEEN 35000 AND 30000;
```

[문제](https://sqlzoo.net/wiki/SELECT_Quiz)

-   Select the code which produces this table

```
SELECT name, population WHERE world WHERE population BETWEEN 1000000 AND 1240000;
```

-   Pick the result you would obtain from this code:

```
SELECT name, population FROM world WHERE name LIKE "Al%";
```

-   Select the code which shows the countries that end in A or L

```
SELECT name FROM world WHERE name LIKE '%a OR name LIKE '%l';
```

-   Pick the result from the query

```
SELECT name, length(name) FROM world WHERE length(name)=5 and region='Europe';
```

-   Here are the first few rows of the world table:

```
SELECT name, area*2 FROM world WHERE population = 64000;
```

-   Select the code that would show the countries with an area larger than 50000 and a population smaller than 10000000

```
SELECT name, area, population FROM world area > 50000 AND population > 10000000;
```

-   Select the code that shows the population density of China, Australia, Nigeria and France

```
SELECT name, population/area FROM world WHERE name IN ('China', 'Nigeria', 'France', 'Australia');
```

### SELECT from world

[학습](https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial)

-   Observe the result of running this SQL command to show the name, continent and population of all countries.

```
SELECT name, continent, population FROM world;
```

-   Show the name for the countries that have a population of at least 200 million. 200 million is 200000000, there are eight zeros.

```
SELECT name FROM world WHERE population > 20000000
```

-   Give the name and the per capita GDP for those countries with a population of at least 200 million.

```
select name, gdp/population as oneGDP from world where population > 200000000
```

-   Show the name and population in millions for the countries of the continent 'South America'. Divide the population by 1000000 to get population in millions.

```
select name, population/100000 as population from world where continent in ('South America');
```

-   Show the name and population for France, Germany, Italy

```
select name, population from world where name in ('France', 'Germany', 'Italy');
```

-   Show the countries which have a name that includes the word 'United'

```
select name from world where name like '%United%';
```

'United'라는 단어가 포함된 이름을 가진 국가를 표시합니다.
WHERE name LIKE '%a OR name LIKE '%l';

-   Two ways to be big: A country is big if it has an area of more than 3 million sq km or it has a population of more than 250 million.
-   Show the countries that are big by area or big by population. Show name, population and area.

```
select name, population, area from world where area > 3000000 OR population > 250000000;
```

-   Exclusive OR (XOR). Show the countries that are big by area (more than 3 million) or big by population (more than 250 million) but not both. Show name, population and area.

1. Australia has a big area but a small population, it should be included.
2. Indonesia has a big population but a small area, it should be included.
3. China has a big population and big area, it should be excluded.
4. United Kingdom has a small population and a small area, it should be excluded.

```
select name, population, area from world where NOT(area > 300000 OR population > 250000000)
```

-   Show the name and population in millions and the GDP in billions for the countries of the continent 'South America'. Use the ROUND function to show the values to two decimal places.

For South America show population in millions and GDP in billions both to 2 decimal places.

```
select name, ROUND(population/1000000, 2) as population, ROUND(gdp/1000000000, 2) as gdp from world where continent in ('South America');
```

-   Show the name and per-capita GDP for those countries with a GDP of at least one trillion (1000000000000; that is 12 zeros). Round this value to the nearest 1000.
    Show per-capita GDP for the trillion dollar countries to the nearest $1000.

```
select name, ROUND(gdp/population, -3) as gdp from world where gdp > 1000000000000;
```

-   Greece has capital Athens.

Each of the strings 'Greece', and 'Athens' has 6 characters.

Show the name and capital where the name and the capital have the same number of characters.

You can use the LENGTH function to find the number of characters in a string
For Microsoft SQL Server the function LENGTH is LEN

```
SELECT name, LEN(name), continent, LEN(continent), capital, LEN(capital)
  FROM world
 WHERE name LIKE 'G%'
```

-   The capital of Sweden is Stockholm. Both words start with the letter 'S'.

Show the name and the capital where the first letters of each match. Don't include countries where the name and the capital are the same word.
You can use the function LEFT to isolate the first character.
You can use <> as the NOT EQUALS operator.

```
SELECT name, LEFT(name,1), capital
FROM world where left(name, 1) <> name
```

[문제](https://sqlzoo.net/wiki/BBC_QUIZ)

-   1. Select the code which gives the name of countries beginning with U

```
select name from world where name like 'U%'
```

-   2. Select the code which shows just the population of United Kingdom?

```
SELECT name FROM world WHERE name = 'United Kingdom';
```

-   3. Select the answer which shows the problem with this SQL code - the intended result should be the continent of France:

```
 SELECT continent
   FROM world
  WHERE 'name' = 'France'
```

-   4. Select the result that would be obtained from the following code:

```
 SELECT name, population / 10
  FROM world
 WHERE population < 10000
```

-   5. Select the code which would reveal the name and population of countries in Europe and Asia

```
SELECT name, population
  FROM world
 WHERE continent IN ('Europe', 'Asia')
```

-   6. Select the code which would give two rows

```
SELECT name FROM world
 WHERE name IN ('Cuba', 'Togo')
```

-   7. Select the result that would be obtained from this code:

```
SELECT name FROM world
 WHERE continent = 'South America'
   AND population > 40000000
```

### SELECT from nobel

[학습](https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial)

-   Change the query shown so that it displays Nobel prizes for 1950.

```
select yr, subject, winner from nobel where yr = 1950
```

-   Show who won the 1962 prize for literature.

```
select winner from nobel where subject = 'Literature' AND yr = 1962;
```

-   Show the year and subject that won 'Albert Einstein' his prize.

```
select yr, subject from nobel where winner = 'Albert Einstein';
```

-   Give the name of the 'peace' winners since the year 2000, including 2000.

```
select winner from nobel where yr >= 2000 AND subject = 'peace';
```

-   Show all details (yr, subject, winner) of the literature prize winners for 1980 to 1989 inclusive.

```
select yr, subject, winner from nobel where 1980 <= yr AND 1989 >= yr AND subject = 'Literature';
```

-   Show all details of the presidential winners:

```
select * from nobel where winner in ('Theodore Roosevelt', 'Thomas Woodrow Wilson', 'Jimmy Carter', 'Barack Obama');
```

-   Show the winners with first name John

```
select winner from nobel where winner like 'John%'
```

-   Show the year, subject, and name of physics winners for 1980 together with the chemistry winners for 1984.

```
select yr, subject, winner from nobel where (subject = 'physics' AND yr = '1980') OR (subject = 'chemistry' AND yr = '1984')
```

-   Show the year, subject, and name of winners for 1980 excluding chemistry and medicine

```
select yr, subject, winner from nobel where NOT(subject = 'chemistry' OR subject = 'medicine') AND yr = '1980'
```

-   Show year, subject, and name of people who won a 'Medicine' prize in an early year (before 1910, not including 1910) together with winners of a 'Literature' prize in a later year (after 2004, including 2004)

```
select yr, subject, winner from nobel where (yr < 1910 AND subject = 'medicine') OR (yr >= 2004 AND subject = 'literature');
```

-   Find all details of the prize won by PETER GRÜNBERG

```
select * from nobel where winner = 'PETER GRÜNBERG'
```

-   Find all details of the prize won by EUGENE O'NEILL

```
select * from nobel where winner = 'EUGENE O''NEILL'
```

-   List the winners, year and subject where the winner starts with Sir. Show the the most recent first, then by name order.

```
select winner, yr, subject from nobel where winner like 'Sir%' order by yr DESC, winner;
```

-   The expression subject IN ('chemistry','physics') can be used as a value - it will be 0 or 1.

Show the 1984 winners and subject ordered by subject and winner name; but list chemistry and physics last.

```

```

-   1. Pick the code which shows the name of winner's names beginning with C and ending in n

```
select winner from nobel where winner like 'c&' AND winner like '%n';
```

-   2. Select the code that shows how many Chemistry awards were given between 1950 and 1960

```
SELECT COUNT(subject) FROM nobel
 WHERE subject = 'Chemistry'
   AND yr BETWEEN 1950 and 1960
```

-   3. Pick the code that shows the amount of years where no Medicine awards were given

```
SELECT COUNT(DISTINCT yr) FROM nobel
 WHERE yr NOT IN (SELECT DISTINCT yr FROM nobel WHERE subject = 'Medicine')
```

-   4. Select the result that would be obtained from the following code:
-   5. Select the code which would show the year when neither a Physics or Chemistry award was given

```
SELECT yr FROM nobel
 WHERE yr NOT IN(SELECT yr
                   FROM nobel
                 WHERE subject IN ('Chemistry','Physics'))
```

-   6. Select the code which shows the years when a Medicine award was given but no Peace or Literature award was

```
SELECT DISTINCT yr
  FROM nobel
 WHERE subject='Medicine'
   AND yr NOT IN(SELECT yr FROM nobel
                  WHERE subject='Literature')
   AND yr NOT IN (SELECT yr FROM nobel
                   WHERE subject='Peace')
```

-   7. Pick the result that would be obtained from the following code:

### SELECT in SELECT

[학습](https://sqlzoo.net/wiki/SELECT_within_SELECT_Tutorial)

-   List each country name where the population is larger than that of 'Russia'.

```
select name from world where population > (select population from world where name = 'Russia')
```

-   Show the countries in Europe with a per capita GDP greater than 'United Kingdom'.

```
select name from world where continent = 'Europe' AND gdp/population > (select gdp/population from world where name = 'United Kingdom')
```

-   List the name and continent of countries in the continents containing either Argentina or Australia. Order by name of the country.

```
select name, continent from world where continent = (select continent from world where name = 'Argentina') OR continent = (select continent from world where name = 'Australia')
```

-   Which country has a population that is more than United Kingdom but less than Germany? Show the name and the population.

```
select name, population from world where population > (select population from world where name = 'United Kingdom') AND population < (select population from world where name = 'Germany')
```

-   Germany (population 80 million) has the largest population of the countries in Europe. Austria (population 8.5 million) has 11% of the population of Germany.
    Show the name and the population of each country in Europe. Show the population as a percentage of the population of Germany.
    You can use the function ROUND to remove the decimal places.
    You can use the function CONCAT to add the percentage symbol.

```
select name, concat(cast(round(population/(select max(population) from world where continent = 'Europe')*100,0) as integer), '%') as percentage from world where continent = 'Europe'
```

-   Which countries have a GDP greater than every country in Europe? [Give the name only.] (Some countries may have NULL gdp values)

```
select name from world where gdp/population > (select sum(gdp/population) / count(select continent from world where continent = 'Europe') as gdp from world where continent = 'Europe')
```

### Using SUM, Count, MAX, DISTINCT and ORDER BY

[학습](https://sqlzoo.net/wiki/Using_SUM,_Count,_MAX,_DISTINCT_and_ORDER_BY)

-   The total population and GDP of Europe.

```
select sum(population), sum(gdp) from bbc where region = 'Europe';
```

-   What are the regions?

```
select distinct region from bbc
```

-   Show the name and population for each country with a population of more than 100000000. Show countries in descending order of population.

```
select name, population from bbc where population >= 100000000 order by population desc
```

### SUM and COUNT

[학습](https://sqlzoo.net/wiki/SUM_and_COUNT)

-   Show the total population of the world.

```
select sum(population) as world population from world;
```

-   List all the continents - just once each.

```
select distinct continent from world
```

-   Give the total GDP of Africa

```
select sum(gdp) as gdp from world where continent = 'Africa'
```

-   How many countries have an area of at least 1000000

```
select count(name) as length from world where area >= 1000000
```

-   What is the total population of ('Estonia', 'Latvia', 'Lithuania')

```
select sum(population) from world where name in ('Estonia', 'Latvia', 'Lithuania')
```

-   For each continent show the continent and number of countries.

```
select continent, count(name) from world group by continent;
```

-   For each continent show the continent and number of countries with populations of at least 10 million.

```
select continent, count(name) from world group by continent having sum(population) > 10000000
```

-   List the continents that have a total population of at least 100 million.

```
select continent, count(name) from world where population >=10000000 group by continent
```

### SUM and COUNT Quiz

-   1. Select the statement that shows the sum of population of all countries in 'Europe'

```
select sum(population) from bbc where region = 'Europe'
```

-   2. Select the statement that shows the number of countries with population smaller than 150000

```
select count(name) from bbc where population < 150000
```

-   3. Select the list of core SQL aggregate functions

```
AVG(), COUNT(), CONCAT(), FIRST(), LAST(), MAX(), MIN(), SUM()
```

-   5. Select the statement that shows the average population of 'Poland', 'Germany' and 'Denmark'

```
 SELECT AVG(population) FROM bbc WHERE name IN ('Poland', 'Germany', 'Denmark')
```
