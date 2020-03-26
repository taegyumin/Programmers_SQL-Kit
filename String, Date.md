# String, Date

## 루시와 엘라 찾기
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59046)

### 나의 답안
	SELECT ANIMAL_ID, NAME, SEX_UPON_INTAKE
	FROM ANIMAL_INS
	WHERE NAME IN ("Lucy", "Ella", "Pickle", "Rogan", "Sabrina", "Mitty")
	ORDER BY ANIMAL_ID;
	
## 이름에 el이 들어가는 동물 찾기
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59047)

### 나의 답안
	SELECT ANIMAL_ID, NAME
	FROM ANIMAL_INS
	WHERE (NAME LIKE "%EL%" AND ANIMAL_TYPE = 'Dog')
	ORDER BY NAME ASC;

## 중성화 여부 파악하기
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59409)

### 나의 답안
	SELECT ANIMAL_ID, NAME, 
	    CASE
	        WHEN ((SEX_UPON_INTAKE LIKE "%Neutered%") OR (SEX_UPON_INTAKE LIKE "%Spayed%")) THEN 'O'
	        ELSE 'X'
	    END AS `중성화`
	    FROM ANIMAL_INS
	    ORDER BY ANIMAL_ID ASC;
	   
## 오랜 기간 보호한 동물 (2)
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59411)

### 나의 답안
	SELECT ANIMAL_OUTS.ANIMAL_ID, ANIMAL_OUTS.NAME
	FROM ANIMAL_INS
	JOIN ANIMAL_OUTS
	ON ANIMAL_INS.ANIMAL_ID = ANIMAL_OUTS.ANIMAL_ID
	ORDER BY (ANIMAL_OUTS.DATETIME - ANIMAL_INS.DATETIME) DESC
	LIMIT 2;
	
## DATETIME에서 DATE로 형 변환
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59414)

### 나의 답안
	SELECT ANIMAL_ID, NAME, date_format(DATETIME, '%Y-%m-%d') AS `날짜`
	FROM ANIMAL_INS;