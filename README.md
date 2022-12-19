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
