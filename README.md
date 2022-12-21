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

스웨덴의 수도는 스톡홀름입니다. 두 단어 모두 문자 'S'로 시작합니다.

각각의 첫 글자가 일치하는 이름과 대문자를 표시합니다. 이름과 대문자가 같은 단어인 국가는 포함하지 마십시오.
LEFT 함수를 사용하여 첫 번째 문자를 분리할 수 있습니다.
NOT EQUALS 연산자로 <>를 사용할 수 있습니다.
