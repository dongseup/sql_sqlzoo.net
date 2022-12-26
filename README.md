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

- Select the code which produces this table

```
SELECT name, population WHERE world WHERE population BETWEEN 1000000 AND 1240000;
```

- Pick the result you would obtain from this code:

```
SELECT name, population FROM world WHERE name LIKE "Al%";
```

- Select the code which shows the countries that end in A or L

```
SELECT name FROM world WHERE name LIKE '%a OR name LIKE '%l';
```

- Pick the result from the query

```
SELECT name, length(name) FROM world WHERE length(name)=5 and region='Europe';
```

- Here are the first few rows of the world table:

```
SELECT name, area*2 FROM world WHERE population = 64000;
```

- Select the code that would show the countries with an area larger than 50000 and a population smaller than 10000000

```
SELECT name, area, population FROM world area > 50000 AND population > 10000000;
```

- Select the code that shows the population density of China, Australia, Nigeria and France

```
SELECT name, population/area FROM world WHERE name IN ('China', 'Nigeria', 'France', 'Australia');
```

### SELECT from world

[학습](https://sqlzoo.net/wiki/SELECT_from_WORLD_Tutorial)

- Observe the result of running this SQL command to show the name, continent and population of all countries.

```
SELECT name, continent, population FROM world;
```

- Show the name for the countries that have a population of at least 200 million. 200 million is 200000000, there are eight zeros.

```
SELECT name FROM world WHERE population > 20000000
```

- Give the name and the per capita GDP for those countries with a population of at least 200 million.

```
select name, gdp/population as oneGDP from world where population > 200000000
```

- Show the name and population in millions for the countries of the continent 'South America'. Divide the population by 1000000 to get population in millions.

```
select name, population/100000 as population from world where continent in ('South America');
```

- Show the name and population for France, Germany, Italy

```
select name, population from world where name in ('France', 'Germany', 'Italy');
```

- Show the countries which have a name that includes the word 'United'

```
select name from world where name like '%United%';
```

'United'라는 단어가 포함된 이름을 가진 국가를 표시합니다.
WHERE name LIKE '%a OR name LIKE '%l';

- Two ways to be big: A country is big if it has an area of more than 3 million sq km or it has a population of more than 250 million.
- Show the countries that are big by area or big by population. Show name, population and area.

```
select name, population, area from world where area > 3000000 OR population > 250000000;
```

- Exclusive OR (XOR). Show the countries that are big by area (more than 3 million) or big by population (more than 250 million) but not both. Show name, population and area.

1. Australia has a big area but a small population, it should be included.
2. Indonesia has a big population but a small area, it should be included.
3. China has a big population and big area, it should be excluded.
4. United Kingdom has a small population and a small area, it should be excluded.

```
select name, population, area from world where NOT(area > 300000 OR population > 250000000)
```

- Show the name and population in millions and the GDP in billions for the countries of the continent 'South America'. Use the ROUND function to show the values to two decimal places.

For South America show population in millions and GDP in billions both to 2 decimal places.

```
select name, ROUND(population/1000000, 2) as population, ROUND(gdp/1000000000, 2) as gdp from world where continent in ('South America');
```

- Show the name and per-capita GDP for those countries with a GDP of at least one trillion (1000000000000; that is 12 zeros). Round this value to the nearest 1000.
  Show per-capita GDP for the trillion dollar countries to the nearest $1000.

```
select name, ROUND(gdp/population, -3) as gdp from world where gdp > 1000000000000;
```

- Greece has capital Athens.

Each of the strings 'Greece', and 'Athens' has 6 characters.

Show the name and capital where the name and the capital have the same number of characters.

You can use the LENGTH function to find the number of characters in a string
For Microsoft SQL Server the function LENGTH is LEN

```
SELECT name, LEN(name), continent, LEN(continent), capital, LEN(capital)
  FROM world
 WHERE name LIKE 'G%'
```

- The capital of Sweden is Stockholm. Both words start with the letter 'S'.

Show the name and the capital where the first letters of each match. Don't include countries where the name and the capital are the same word.
You can use the function LEFT to isolate the first character.
You can use <> as the NOT EQUALS operator.

```
SELECT name, LEFT(name,1), capital
FROM world where left(name, 1) <> name
```

[문제](https://sqlzoo.net/wiki/BBC_QUIZ)

- 1. Select the code which gives the name of countries beginning with U

```
select name from world where name like 'U%'
```

- 2. Select the code which shows just the population of United Kingdom?

```
SELECT name FROM world WHERE name = 'United Kingdom';
```

- 3. Select the answer which shows the problem with this SQL code - the intended result should be the continent of France:

```
 SELECT continent
   FROM world
  WHERE 'name' = 'France'
```

- 4. Select the result that would be obtained from the following code:

```
 SELECT name, population / 10
  FROM world
 WHERE population < 10000
```

- 5. Select the code which would reveal the name and population of countries in Europe and Asia

```
SELECT name, population
  FROM world
 WHERE continent IN ('Europe', 'Asia')
```

- 6. Select the code which would give two rows

```
SELECT name FROM world
 WHERE name IN ('Cuba', 'Togo')
```

- 7. Select the result that would be obtained from this code:

```
SELECT name FROM world
 WHERE continent = 'South America'
   AND population > 40000000
```

### SELECT from nobel

[학습](https://sqlzoo.net/wiki/SELECT_from_Nobel_Tutorial)

- Change the query shown so that it displays Nobel prizes for 1950.

```
select yr, subject, winner from nobel where yr = 1950
```

- Show who won the 1962 prize for literature.

```
select winner from nobel where subject = 'Literature' AND yr = 1962;
```

- Show the year and subject that won 'Albert Einstein' his prize.

```
select yr, subject from nobel where winner = 'Albert Einstein';
```

- Give the name of the 'peace' winners since the year 2000, including 2000.

```
select winner from nobel where yr >= 2000 AND subject = 'peace';
```

- Show all details (yr, subject, winner) of the literature prize winners for 1980 to 1989 inclusive.

```
select yr, subject, winner from nobel where 1980 <= yr AND 1989 >= yr AND subject = 'Literature';
```

- Show all details of the presidential winners:

```
select * from nobel where winner in ('Theodore Roosevelt', 'Thomas Woodrow Wilson', 'Jimmy Carter', 'Barack Obama');
```

- Show the winners with first name John

```
select winner from nobel where winner like 'John%'
```

- Show the year, subject, and name of physics winners for 1980 together with the chemistry winners for 1984.

```
select yr, subject, winner from nobel where (subject = 'physics' AND yr = '1980') OR (subject = 'chemistry' AND yr = '1984')
```

- Show the year, subject, and name of winners for 1980 excluding chemistry and medicine

```
select yr, subject, winner from nobel where NOT(subject = 'chemistry' OR subject = 'medicine') AND yr = '1980'
```

- Show year, subject, and name of people who won a 'Medicine' prize in an early year (before 1910, not including 1910) together with winners of a 'Literature' prize in a later year (after 2004, including 2004)

```
select yr, subject, winner from nobel where (yr < 1910 AND subject = 'medicine') OR (yr >= 2004 AND subject = 'literature');
```

- Find all details of the prize won by PETER GRÜNBERG

```
select * from nobel where winner = 'PETER GRÜNBERG'
```

- Find all details of the prize won by EUGENE O'NEILL

```
select * from nobel where winner = 'EUGENE O''NEILL'
```

- List the winners, year and subject where the winner starts with Sir. Show the the most recent first, then by name order.

```
select winner, yr, subject from nobel where winner like 'Sir%' order by yr DESC, winner;
```

- The expression subject IN ('chemistry','physics') can be used as a value - it will be 0 or 1.

Show the 1984 winners and subject ordered by subject and winner name; but list chemistry and physics last.

```

```

이름이 John인 우승자 표시
1980년 물리학 우승자의 연도, 주제 및 이름을 1984년 화학 우승자와 함께 표시하십시오.
화학 및 의학을 제외한 1980년 수상자 연도, 주제 및 이름 표시
초기 연도(1910년 이전, 1910년 제외)에 '의학' 상을 수상한 사람과 후기 연도(2004년 이후, 2004년 포함) '문학' 상을 수상한 사람의 연도, 주제 및 이름 표시
PETER GRÜNBERG가 수상한 상품에 대한 모든 세부 정보 찾기
그의 이름에 있는 u에는 움라우트가 있습니다. 이 링크가 유용할 수 있습니다 https://en.wikipedia.org/wiki/%C3%9C#Keyboarding
EUGENE O'NEILL이 수상한 상품에 대한 모든 세부 정보 찾기

우승자가 Sir로 시작하는 우승자, 연도 및 주제를 나열하십시오. 가장 최근의 것을 먼저 표시한 다음 이름순으로 표시합니다.

표현 대상 IN('chemistry','physics')은 값으로 사용할 수 있습니다. 0 또는 1이 됩니다. 1984년 우승자와 주제를 주제와 우승자 이름으로 정렬하여 표시합니다. 그러나 화학과 물리학은 마지막에 나열하십시오.
