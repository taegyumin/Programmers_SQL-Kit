# GROUP BY

## 고양이와 개는 몇 마리 있을까
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59040)

### 나의 답안
	SELECT ANIMAL_TYPE, count(ANIMAL_TYPE) FROM ANIMAL_INS GROUP BY ANIMAL_TYPE ORDER BY ANIMAL_TYPE ASC;
	
## 동명 동물 수 찾기
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59041)

### 나의 답안
	SELECT NAME, count(NAME) as `COUNT` FROM ANIMAL_INS where NAME IS NOT NULL GROUP BY NAME HAVING `COUNT`>1 ORDER BY NAME ASC;
	
## 입양 시각 구하기 (1)
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59412)

### 나의 답안
	SELECT HOUR(DATETIME) AS `HOUR`, COUNT(HOUR(DATETIME)) AS `COUNT` FROM ANIMAL_OUTS GROUP BY HOUR(DATETIME) HAVING `HOUR`>=9 and`HOUR`<=19 ORDER BY `HOUR`;
	
## 입양 시각 구하기 (2)
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59413)

### 나의 답안
	select hour, sum(count) from (
	    select 0 as hour, 0 as count
	    union 
	    select A.* from (
	        select @hour := @hour + 1 as hour, A.* 
	            from (select 0 as count from animal_outs) A, ( select @hour := 0) b
	        limit 23
	    ) A
	    union
	     SELECT HOUR(DATETIME) AS HOUR, COUNT(*) AS COUNT FROM ANIMAL_OUTS
	     GROUP BY HOUR HAVING HOUR BETWEEN 0 AND 23
	     order by hour
	) A
	group by hour
	order by 1;
