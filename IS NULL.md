# IS NULL

## 이름이 없는 동물의 아이디
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59039)

### 나의 답안
	SELECT ANIMAL_ID FROM ANIMAL_INS WHERE NAME IS NULL ORDER BY ANIMAL_ID;
	
## 이름이 있는 동물의 아이디
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59407)

### 나의 답안
	SELECT ANIMAL_ID AS ID FROM ANIMAL_INS WHERE NAME IS NOT NULL ORDER BY ID ASC;
	
## NULL 처리하기
[문제 설명](https://programmers.co.kr/learn/courses/30/lessons/59410)

### 나의 답안
	SELECT ANIMAL_TYPE, 
	    CASE 
	        WHEN (NAME is NULL) THEN "No name"
	        ELSE NAME
	    END AS "NAME", SEX_UPON_INTAKE FROM ANIMAL_INS ORDER BY ANIMAL_ID;