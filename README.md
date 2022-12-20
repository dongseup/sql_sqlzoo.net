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
