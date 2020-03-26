# JOIN
## 없어진 기록 찾기
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59042)

### 나의 답안
	SELECT ANIMAL_OUTS.ANIMAL_ID, ANIMAL_OUTS.NAME
	FROM ANIMAL_OUTS
	LEFT JOIN ANIMAL_INS
	ON ANIMAL_OUTS.ANIMAL_ID = ANIMAL_INS.ANIMAL_ID
	WHERE ANIMAL_INS.ANIMAL_ID IS NULL
	ORDER BY ANIMAL_OUTS.ANIMAL_ID;

## 있었는데요 없었습니다
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59043)

### 나의 답안
	SELECT ANIMAL_OUTS.ANIMAL_ID, ANIMAL_OUTS.NAME
	FROM ANIMAL_OUTS
	JOIN ANIMAL_INS
	ON ANIMAL_OUTS.ANIMAL_ID = ANIMAL_INS.ANIMAL_ID
	WHERE ANIMAL_OUTS.DATETIME < ANIMAL_INS.DATETIME
	ORDER BY ANIMAL_INS.DATETIME;

## 오랜 기간 보호한 동물 (1)
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59044)

### 나의 답안
	SELECT ANIMAL_INS.NAME, ANIMAL_INS.DATETIME
	FROM ANIMAL_INS
	LEFT JOIN ANIMAL_OUTS
	ON ANIMAL_OUTS.ANIMAL_ID = ANIMAL_INS.ANIMAL_ID
	WHERE ANIMAL_OUTS.ANIMAL_ID IS NULL
	ORDER BY ANIMAL_INS.DATETIME
	LIMIT 3;
	
## 보호소에서 중성화한 동물
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59045)

### 나의 답안
	SELECT ANIMAL_OUTS.ANIMAL_ID, ANIMAL_OUTS.ANIMAL_TYPE, ANIMAL_OUTS.NAME
	FROM ANIMAL_OUTS
	INNER JOIN ANIMAL_INS
	ON ANIMAL_OUTS.ANIMAL_ID = ANIMAL_INS.ANIMAL_ID
	WHERE (ANIMAL_INS.SEX_UPON_INTAKE LIKE "%Intact%")
	AND (ANIMAL_OUTS.SEX_UPON_OUTCOME LIKE "%Spayed%" OR ANIMAL_OUTS.SEX_UPON_OUTCOME LIKE "%Neutered%")
	ORDER BY ANIMAL_ID ASC;