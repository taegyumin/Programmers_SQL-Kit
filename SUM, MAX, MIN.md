# SUM, MAX, MIN

## 최댓값 구하기
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59415)

### 나의 답안
	SELECT max(DATETIME) FROM ANIMAL_INS;
	
## 최솟값 구하기
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59038)

### 나의 답안
	SELECT min(DATETIME) FROM ANIMAL_INS;

## 동물 수 구하기
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59406)

### 나의 답안
	SELECT count(ANIMAL_ID) FROM ANIMAL_INS;
	
## 중복 제거하기
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59408)

### 나의 답안
	SELECT COUNT(DISTINCT NAME) AS `count`
	FROM ANIMAL_INS 
	WHERE NAME IS NOT NULL;