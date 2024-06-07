# 개발자를 위한 SQL 데이터베이스

속성: 토픽
교과목: 데이터베이스와 SQL
기한: 2024년 6월 4일
상태: 진행 중

# 🍀 **개발자를 위한 SQL 데이터베이스**

## 1 장 | **SQL로 하는 데이터 분석**

---

### 0절. 단축키

- Windows SQL문 실행 : `Ctrl + Shift + Enter`
- ctrl + T : 새 쿼리창 열기

### 1절. **데이터베이스 기본 개념**

- **테이블** : 표 형식으로 저장된 데이터의 집합
    - row(행) : 하나의 개체를 나타내는 것
    - column(열) : 개체의 각 속성을 나타내는 것
    
- **DBMS (Data Base Management System)** : 데이터베이스를 운영하고 관리하는 소프트웨어
    
    ![Untitled](%E1%84%80%E1%85%A2%E1%84%87%E1%85%A1%E1%86%AF%E1%84%8C%E1%85%A1%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20SQL%20%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%E1%84%87%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%89%E1%85%B3%20ab1e2dce677845129206f5db596a784e/Untitled.png)
    
    - SQL (Structured Query Language) 사용
    - cf) Oracle은 '오라클'과 'MySQL'을 모두 갖고 있는 회사
    
- **서버-클라이언트 구조** : 서버 역할을 하는 하나의 프로그램이 실행되고 있고, 사용자는 클라이언트 역할을 하는 프로그램(DBMS)으로 해당 서버에 접속하고, 그 서버에 SQL을 전송해서 명령을 내리는 구조

### 2절. **테이블 생성하기**

- 데이터베이스 생성하기 `CREATE DATABASE database_name`
- CSV: Comma Separated Values
- Primary Key(기본키) : 테이블에서 하나의 row를 고유하게 식별할 수 있도록 해주는 column(열쇠모양)
    - Natural Key
        
        실제로 어떤 개체가 갖고 있는 속성을 나타내는 컬럼이 Primary Key가 됐을 때 (ex, 주민등록번호, ISBN)
        
    - Surrogate Key
        
        어떤 개체의 실제 속성은 아니지만 Primary Key로 쓰기 위해 추가한 컬럼. 주로 1부터 순차적으로 증가하는 숫자가 들어가게 됨
        
    - NN : NOT NULL, 값이 무조건 존재해야 함
    - AI : Auto Increment
- NULL : 값이 존재하지 않은 상태

### 3절. **데이터 조회로 기본 다지기**

- * : asterisk, 전체
- **SELECT**
    
    USE copang_main; SELECT column FROM table WHERE 조건;
    
    SELECT column FROM database.table WHERE 조건; 
    
- **WHERE**
    - **비교 연산**
        - WHERE age NOT BETWEEN 30 AND 39; // 30대 가 아닌 경우의 나이칼럼
        - WHERE sign_up_day > '2019-01-01'; //2019년부터 가입한 사람들
    
    - **논리연산** : AND의 우선순위가 OR보다 높다
    
    - **유무 확인** IN
        
        ex) `WHERE age IN (20, 30)`
        
    
    - **문자열 패턴 매칭**
        - WHERE address LIKE '서울%';	//문자열에 서울+a이 있는 경우
        - WHERE address LIKE '%서울% ';	//서울이 있는 경우
        - WHERE email LIKE 'c_____@%';	//c로 시작하는 6글자만, _:임의의 한 글자
            
            -> [codeit@naver.com](mailto:codeit@naver.com)
            
    
    - **DATE 타입 관련 함수**
        - YEAR(birthday) //년도
        - MONTH(sign_up_day) //달
        - DAYOFMONTH(sign_up_day) //일
        - CURDATE() : 오늘 날짜
        - DATEDIFF(A, B) : A-B
        - DATE_ADD(A, INTERVAL B DAY) : A에서 B일 이후의 날짜
        - DATE_SUB(A, INTERVAL B DAY) : A에서 B일 이전의 날짜
        - UNIX_TIMESTAMP(sign_up_day) : 1970년 1월 1일을 기준으로 sign_up_day가 총 몇 초가 지났는지
        - UNIXTIME(unix_timestamp) : total second -> DATETIME type (sec로 표현 됨)
        
    - **데이터 정렬하기 ORDER BY**
        - ORDER BY height ASC; //오름차순, 디폴트
            
            ORDER BY height DESC; //내림차순
            
        - 정렬은 순서대로! - 가입연도 내림차순, 가입연도가 같으면 오름차순 정렬
            
            ORDER BY YEAR(sign_up_day) DESC, email ASC;
            
    - **데이터 일부만 추리기 LIMIT**
        - limit은 제일 마지막에 적는다
        - LIMIT 10 ; // 10개 만
            
            LIMIT 8, 2; // 9,10번 째 row만
            
    - **데이터 타입 일시적으로 변경하기 CAST()**
        
        CAST(data AS signed) // data를 signed (INT)로 변환
        
        CAST(data AS decimal) // data를 decimal (floating point)로 변환
        
    - **이스케이핑(escaping)** : 표현식을 일반 텍스트로 표현하고 싶을 때 앞에 \를 붙여줌
    
    - **ci(case-insensitive)** : 문자열이 동일한지 확인할 때, 대소문자를 구별하지 않음
    → **BINARY** '%g%' 처럼 쓰면 대소문자 구분 가능

### 4절. 데이터 분석 단계로 나아가기

- **집계 함수(Aggregate Function)**
    - COUNT(col)
        - COUNT(*) : 전체 row
        - null 개수는 제외하고 count함
    - AVG(col)
        - null은 제외하고 구함
    - MAX(col), MIN(col)
    - SUM()
    - STD() - 표준편차
    
- **산술 함수(Mathematical Function)**
    - ABS() 함수 - 절대값
    - SQRT() 함수 - 제곱근
    - CEIL() 함수 - 올림
    - FLOOR() 함수 - 내림
    - ROUND() 함수 - 반올림
    
- **NULL 처리**
    - IS NOT NULL
    - COALESECE(col, A) - col이 NULL 이라면 A 리턴, 아니면 원래 값 리턴
    - NULL에는 어떤 연산을 해도 NULL
    - NULL은 어떤 값이 아니기 때문에 등호(=)를 사용해서 비교할 수 없음.
    - cf) dbms마다 null이 가장 큰 값이 될 때도 있고 가장 작은 값이 될 때도 있음.
    
- **산술 계산** / : 나누기(몫 계산)
- **ALIAS 붙이기** AS or ' '(공백)
- **요소 붙이기**
    
    `CONCAT(co1, 'com', ',' col2, 'kr') AS '키와 몸무게' // 결과 : col1com, col2kr`
    
- **조건문**
    
    ```sql
    (CASE
    	WHEN 조건 THEN 결과
    	WHEN 조건 THEN 결과
    	ELSE 결과
    END) AS 칼럼명
    ```
    

- **고유값만 보기 DISTINCT(col)**
- **문자열 함수**
    - SUBSTRING(col, a, b)) : a번째 글자부터 b글자 추출
    - LENGTH() : 문자열의 길이
    - UPPER() : 문자열 대문자로 바꾸기
    - LOWER() : 문자열 소문자로 바꾸기
    - LPAD(col, totalNUM, W) : col의 값을, 왼쪽에 W을 붙여서 총 totalNUM자리로 만드는 함수, ex) `RPAD(age,10, '!') // 29!!!!!!!!`
    - TRIM(), LTRIM(), RTRIM() : 문자열에 존재하는 공백을 제거
    
- **그루핑 GROUP BY**
    - SELECT 절에는 GROUP BY 뒤에서 사용한 컬럼들 또는 COUNT(), MAX() 등과 같은 집계 함수만 쓸 수 있다. GROUP BY 뒤에 쓰지 않은 컬럼 이름을 SELECT 뒤에 쓸 수는 없다.
        - GROUP BY 절 뒤에 쓴 컬럼 이름들만, SELECT 절 뒤에도 쓸 수 있음
        - SELECT 절 뒤에서 집계 함수에 그 외의 컬럼 이름을 인자로 넣는 것은 허용
    - **HAVING ‘조건’**
        - ex) `HAVING age >= 20 AND height >= 170`
        - WHERE는 table에서 row를 조회할 때 사용, HAVING은 이미 조회된 row를 grouping해서 다시 조회할 때!
    
    - **WITH ROLL UP**
        - GROUP BY 뒤의 그루핑 기준들의 등장 순서에 맞춰서 부분 총계를 보여줌
        
    - **GROUPING()**
        - 실제 NULL을 나타내기 위해 쓰인 NULL인 경우에는 0, 부분 총계를 나타내기 위해 표시된 NULL은 1
    
- **SQL 작성 순서와 실행 순서**
    - 작성 순서 : SELECT - FROM - WHERE - GROUP BY - HAVING - ORDER BY - LIMIT
    - 실행 순서 : FROM - WHERE - GROUP BY - HAVING - SELECT - ORDER BY - LIMIT
        - WHERE: 해당 테이블에서 특정 조건(들)을 만족하는 row들만 선별합니다.
        - GROUP BY: row들을 그루핑 기준대로 그루핑합니다. 하나의 그룹은 하나의 row로 표현됩니다.

### 5절. **테이블 조인을 통한 깊이있는 데이터 분석**

- **Foreign Key(외래키) :** 다른 테이블의 특정 row를 식별할 수 있게 해주는 컬럼
    
    ![자식 테이블 - 참조를 하는 테이블인 stock 테이블 
    부모 테이블 - 참조를 당하는 테이블인 item 테이블](%E1%84%80%E1%85%A2%E1%84%87%E1%85%A1%E1%86%AF%E1%84%8C%E1%85%A1%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B1%E1%84%92%E1%85%A1%E1%86%AB%20SQL%20%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%E1%84%87%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%89%E1%85%B3%20ab1e2dce677845129206f5db596a784e/c.png)
    
    자식 테이블 - 참조를 하는 테이블인 stock 테이블 
    부모 테이블 - 참조를 당하는 테이블인 item 테이블
    
    - 설정 방법 : 자식 테이블의 foreign keys로 가서 자식-부모/자식-부모로 설정 후 apply
    - Foreign key로 설정된 컬럼을 기준으로 조인하는 것이 일반적이나, 서로 다른 두 테이블의 컬럼이 같은 의미를 갖고 있다면 Foreign key 관계가 설정되어있지 않아도 조인 가능 (이때 두 컬럼의 데이터 타입은 같아야 함)
    
- **결합 연산과 집합 연산**
    - 결합 연산은 테이블을 가로 방향으로 합치는 것 : JOIN
    - 집합 연산은 테이블을 세로 방향으로 합치는 것 : INTERSECT, MINUS/EXCEPT, UNION
    
- **Alias 붙이기**
    - FROM 절에서 테이블에 alias를 붙이면, 다른 모든 절에서 그 테이블은 그 alias로만 나타내야 한다.
        
        ```sql
        SELECT
        	[i.id](http://i.id/),
        	[i.name](http://i.name/),
        	s.item_id,
        	s.inventory_count
        FROM item AS i LEFT OUTER JOIN stock AS s
        	ON [i.id](http://i.id/) = s.item_id
        
        ```
        
- **USING**
    - 두 테이블에서 조인 조건으로 사용되는 컬럼들의 이름이 같을때 USING(col)을 사용하는 것도 허용
    - `ON old.id = new.id` 대신 `USING(id)`
    
- **결합 연산 : JOIN**
    - OUTER JOIN
        
        ```sql
        FROM item LEFT OUTER JOIN stock
        ON new.id = stock.item_id
        ```
        
        - LEFT OUTER JOIN = > 기준이 되는 테이블이 left에
        - RIGHT OUTER JOIN = > 기준이 되는 테이블이 right에 있음
        - FULL OUTER JOIN =
        
        ```sql
        SELECT *
        FROM item LEFT OUTER JOIN stock
        	ON [item.id](http://item.id/) = stock.item_id
        **UNION (ALL)**
        SELECT *
        FROM item RIGHT OUTER JOIN stock
        	ON [item.id](http://item.id/) = stock.item_id
        ```
        
    - INNER JOIN `FROM item INNER JOIN JOIN stock`
        - 기준이 되는 테이블이 따로 없고 두 테이블 모두 기준 칼럼에 일치하는 값이 있는 로우들만 연결
        
    - NATURAL JOIN `FROM item NATURAL JOIN stock`
        - 두 테이블에서 같은 이름의 컬럼을 찾아서 자동으로 조인 조건을 설정하고, INNER JOIN 함
        
    - CROSS JOIN `FROM item CROSS JOIN stock`
        - 두 테이블의 Cartesian Product를 구하는 조인.
            - 카르테시안 곱(Cartesian Product) : 모든 원소들의 조합을 나타내는 것
    - Non-Equi & Equi 조인
        - Equi 조인 : 조인 조건에 항상 등호(=)를 사용하는 조인; 동등 조건을 판단함.
        - Non-Equi 조인 :  조인 조건에 등호(=)를 사용하지 않는 조인
            
            ```sql
            FROM member LEFT OUTER JOIN item
            ON member.sign_up_day < item.registration_date
            // 회원의 사이트 가입일 이후에 사이트에 올라온 상품
            ```
            
        
- **집합 연산 : INTERSECT, MINUS 또는 EXCEPT, UNION**
    - MySQL에서는 버전 8.0 기준으로 UNION 연산자만 지원
        
        (다른 DBMS인 오라클에서는 3가지 연산자 모두 지원
        
    1. A ∩ B (INTERSECT 연산자 사용)
        
        ```sql
        //INNER JOIN
        SELECT * FROM member_A
        INTERSECT
        SELECT * FROM member_B
        ```
        
    2. A - B (MINUS 연산자 또는 EXCEPT 연산자 사용)
        
        ```sql
        SELECT * FROM member_A
        MINUS
        SELECT * FROM member_B
        
        //LEFT OUTER JOIN, JOIN하는 컬럼을 기준으로, 조인테이블의 값이 NULL인 경우
        SELECT *
        FROM member_A a LEFT OUTER JOIN member_B b
        	ON ([a.ID](http://a.id/) = [b.ID](http://b.id/))
        WHERE [b.ID](http://b.id/) IS NULL;
        ```
        
    3. A U B (UNION 연산자 사용)
        - UNION ALL - 중복 제거 X
        - 두 테이블의 칼럼 구조(총 컬럼의 수, 각 컬럼의 데이터 타입)가 다르면 연산 실패.
            - SELECT <여러 칼럼의 공통 부분> FROM member_A 로 해결 가능
        
        ```sql
        SELECT * FROM member_A
        UNION (ALL)
        SELECT * FROM member_B
        ```
        
    

### 6절. **서브쿼리와 뷰를 활용한 유연한 데이터 분석**

- **서브쿼리** : SQL문 안에 '부품'처럼 들어가는 SELECT 문
    
    sub(하위의, 일부분의), Query (데이터베이스에 보내는 요청)
    
- **서브쿼리의 종류 : 리턴 결과에 따라**
    - 스칼라 서브쿼리 : 단일값 리턴
    - 하나의 column에 여러 row들이 있는 형태의 결과를 리턴하는 서브쿼리
    - derived 테이블 리턴 : 하나의 테이블 형태의 결과(여러 column, 여러 row)를 리턴하는 서브쿼리
        - alias를 꼭 붙여주어야 함
        
- **서브쿼리의 종류 : 독립적인지에 따라**
    - 비상관 서브쿼리 : 그 자체만으로도 실행이 가능한 서브쿼리, outer query와 별개로 독립적으로 실행
    - 상관 서브쿼리 : 서브쿼리가 outer query에 적힌 테이블 이름 등과 상관 관계를 갖고 있어서 그 단독으로는 실행되지 못하는 서브쿼리
    
- **서브쿼리와 함께 사용되는 키워드**
    - IN
        
        ```sql
        SELECT * FROM item
        WHERE id IN(
        	SELECT item_id
        	FROM review
        	GROUP BY item_id HAVING COUNT(*) >= 3
        );
        ```
        
    - ANY/SOME : 서브쿼리의 결과에 있는 각 row의 값들 중 하나라도 조건을 만족하는 경우가 있으면 TRUE 리턴
    - ALL : 모든 경우에 대해서 해당 조건이 성립해야 TRUE를 리턴
    - EXISTS, NOT EXISTS
- **뷰** : 조인 등의 작업을 해서 만든 '결과 테이블'이 가상으로 저장된 형태(가상 테이블)
    - 자주 쓰는 결과를 table로 저장하지만 실제 테이블과 달리 데이터가 물리적으로 컴퓨터에 저장되어 있는 건 아님
    - 뷰 생성하기 `CREATE VIEW '뷰 이름' AS SELECT 문;`
    - 뷰의 장점
        - 높은 편의성 : 복잡한 SQL문을 뷰로 저장해두면 재활용할 수 있어서 편리함
        - 각 직무별 데이터 수요에 알맞은, 다양한 구조의 데이터 분석 기반을 구축 :
            
            기존의 테이블 구조를 건드리지 않고 직무에 따라, 상황에 따라, 필요로 하는 데이터의 종류와 그 구조를 준비할 수 있음
            
        - 데이터 보안 : 분석가에게 민감 정보가 담긴 컬럼을 제외하고 보여줄 수 있음
        
- **데이터베이스 현황 파악**
    - `SHOW DATABASES;` : 존재하는 데이터베이스 파악
    - `SHOW FULL TABLES IN database_name;` : 한 데이터베이스 안의 테이블(뷰도 포함)들 파악
    - `DESCRIBE table_name;` : 한 테이블의 컬럼 구조 파악
    - Foreign Key(외래키) 파악 : Foreign Key 관계가 성립한다고 해도 관리자가 그것을 Foreign Key로 설정하지 않는 경우도 많다. Foreign Key 관련 정보를 조회하는 SQL 문은 DBMS의 기본 데이터베이스에서 그 정보를 가져오는 것이기 때문에 DBMS마다 다르다.

## 2 장 |  **SQL로 하는 데이터 관리**

---

### 1절. **데이터베이스와 테이블 구축**

- **데이터베이스 생성하기** `CREATE DATABASE database`
    - 'database'가 없는 경우를 확인한 후 생성하기 `CREATE DATABASE IF NOT EXIST database`
    
- **사용하는 데이터베이스 지정하기** `USE database`
    - 지정된 데이터베이스 안에 있는 존재를 SQL 문에서 가리킬 때, 데이터베이스 이름을 적어주지 않아도 됨
    
- 칼럼의 데이터 타입 [https://www.codeit.kr/topics/data-management-using-sql/lessons/3263](https://www.codeit.kr/topics/data-management-using-sql/lessons/3263)

- **백틱(backtick)** : MySQL에서 백틱은 해당 단어가 identifier임을 나타내는 기호
    - DBMS에서는 데이터베이스, 테이블, 컬럼 등과 같은 구성요소를 object(객체)라고 하고 이런 object에 붙여준 이름을 identifier(식별자)라고 함
    
- **테이블 생성하기**
    
    ```sql
    CREATE TABLE animal_info (
    	id INT NOT NULL AUTO_INCREMENT,
    	name VARCHAR(10) NOT NULL,
    	age TINYINT NOT NULL,
    	sex CHAR(1) NOT NULL,
    	weight DOUBLE NOT NULL,
    	feature VARCHAR(500) NULL, //null값이 들어와도 됨
    	entry_date DATE NOT NULL,
    	PRIMARY KEY(id)
    );
    ```
    
- **테이블에 row 추가하기**
    
    `INSERT INTO table (col1, col2, ... , coln)` 
    
    `VALUES (v1, v2, ... , vn)`
    
    - 모든 칼럼의 값이 존재한다면 칼럼명을 생략해도 됨.
    `INSERT INTO table VALUES (v1, v2, ... , vn)`
    
- **테이블의 row 갱신하기**
`UPDATE table SET col1 = 'value1', col2 = 'value2' WHERE id = 2;`
    
    (ex) `UPDATE table SET score = score + 3` //score 칼럼에 있는 모든 값에 3 더하기
    
- **테이블의 row 삭제하기**
    - 물리 삭제 vs 논리 삭제
        - 물리 삭제 : row를 바로 삭제 `DELETE FROM table WHERE id = 2;`
        - 논리 삭제 : 삭제해야할 row를 삭제하지 않고, ‘삭제 여부’를 나타내는 별도의 컬럼에 값(Y/N)을 넣는 것 ⇒ `UPDATE`

### 2절. **테이블 다루기**

- **DESCRIBE 또는 DESC**
    - Field : 컬럼의 이름
    - Type : 컬럼의 데이터 타입
    - Null : 컬럼의 Null 속성 유무
    - Key : Primary Key, Unique 속성 여부
    - Default : 컬럼의 기본값
    - Extra : AUTO_INCREMENT 등의 기타 속성
    
- **칼럼 추가하기** `ALTER TABLE table ADD col DATATYPE ATTRIBUTE`
    
    (ex) `ALTER TABLE student ADD gender CHAR(1) NULL;`
    

- **컬럼명 바꾸기** `ALTER TABLE table RENAME COLUMN col_old TO col_new;`
    
    (ex)  `ALTER TABLE student RENAME COLUMN student_number TO registration_number;`
    

- **칼럼 삭제하기** `ALTER TABLE table DROP COLUMN col;`
    
    (ex) `ALTER TABLE student DROP COLUMN admission_date`;
    

- **칼럼 데이터 타입 변경하기** `ALTER TABLE table MODIFY col DATATYPE ATTRIBUTE;`
    - **칼럼에 DEFAULT 값 넣기**
        
        `ALTER TABLE table MODIFY col DATATYPE ATTRIBUTE(N/NN) DEFAULT value;`
        
        - (ex) ALTER TABLE student MODIFY major INT NOT NULL DEFAULT 101;
        - ATTRIBUTE을 명시해주지 않을 경우 NULL로 변경됨(default가 NULL)
    
- **칼럼에 현재 시간 값 넣기**
    
    → 어떤 row가 추가되거나 갱신되었을 때 그 추가 혹은 갱신 시각을 저장해야할 때
    
    (ex) 게시글 업로드 시각, 댓글이 달린 시각, 댓글을 수정한 시각
    
    - **NOW() 함수**
        - 각 row마다 시간값에 관한 처리를 다르게 해줘야하는 경우
            
            (ex) 어떤 row는 현재 시간에서 +3시간, 어떤 row는 현재 시간에서 -5시간을 해줘야하는 경우)
            
        
        ```sql
        INSERT INTO post (title, content, upload_time, recent_modified_time)
        VALUES ("요즘 고민", "집 가고 싶음", NOW(), NOW());
        
        UPDATE post
        SET content = "집에서 나오기 싫음",  recent_modified_time = NOW()
        WHERE id = 1;
        //YYYY-MM-DD HH:MM:SS
        ```
        
    
    - 컬럼에 **DEFAULT CURRENT_TIMESTAMP / ON UPDATE CURRENT_TIMESTAMP** 속성 설정하기
        - 굳이 날짜/시간 값을 별도로 신경쓰기가 싫을 경우 DBMS가 알아서 관리하도록 함
        - DEFAULT CURRENT_TIMESTAMP : 테이블에 새 row를 추가할 때 디폴트로 현재 시간이 설정
        - ON UPDATE CURRENT_TIMESTAMP : 기존 row에서 단 하나의 컬럼이라도 갱신되면 갱신될 때의 시간이 설정
        
        ```sql
        ALTER TABLE post
        MODIFY upload_time DATETIME DEFAULT CURRENT_TIMESTAMP,
        MODIFY recent_modified_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP 
        ON UPDATE CURRENT_TIMESTAMP
        ```
        
    
- **UNIQUE 속성주기** `ALTER TABLE table MODIFY col DATATYPE ATTRIBUTE(N/NN) UNIQUE;`
    
    → 각 row마다 고유한 값을 가져야 할 때
    
    - Primary key vs Unique
        - Primary key는 테이블당 오직 하나만 존재, 한 테이블에 여러 개의 Unique 속성들이 존재 가능
        - Primary Key는 NULL을 가질 수 없지만, Unique는 NULL을 허용한다
        
- **CONSTRAINT(제약사항)**
    - CONSTRAINT 걸기 `ALTER TABLE table ADD CONSTRAINT constraint_name CHECK (조건)`
    - CONSTRAINT 삭제 `ALTER TABLE table DROP CONSTRAINT constraint_name`
    
- **칼럼 작업들**
    - 컬럼 가장 앞으로 당기기 `ALTER TABLE table MODIFY col DATATYPE ATTRIBUTE FIRST;`
    (ex) ALTER TABLE table MODIFY id INT NOT NULL AUTO_INCREMENT FIRST;
    - 컬럼 간의 순서 바꾸기 `ALTER TABLE table MODIFY col1 DATATYPE ATTRIBUTE AFTER col2;`
    - 컬럼의 이름(RENAME)과 컬럼의 데이터 타입 및 속성(MODIFY) 동시에 수정하기
    `ALTER TABLE table CHANGE col_old col_new DATATYPE_new ATTRIBUTE;`
    - 여러 작업 동시에 수행하기
        - Modify랑 Change는 따로 작성하기
        
        ```sql
        ALTER TABLE table
        	RENAME COLUMN col_old TO col_new,
        	MODIFY col DATATYPE_new NOT NULL,
        	DROP COLUMN col2,
        	ADD col3 DOUBLE NOT NULL;
        ```
        
    
- **테이블 이름 변경** `RENAME TABLE table_old TO table_new;`
- **테이블 복사본 만들기** `CREATE TABLE copy_of_table AS SELECT * FROM table;`
    - 테이블 컬럼 구조만 복사하기 `CREATE TABLE copy_of_table LIKE table;`
    - 테이블의 row 복사하기 `INSERT INTO copy_of_table SELECT * FROM table WHERE (조건)`
- **테이블 삭제하기** `DROP TABLE table;`
- **테이블 컬럼 구조만 남기고 데이터 날리기** `TRUNCATE table;` or `DELETE FROM table;`

- **safe update 관련** [https://www.codeit.kr/topics/data-management-using-sql/lessons/3277](https://www.codeit.kr/topics/data-management-using-sql/lessons/3277)
    - safe update 사용 중일 경우, KEY column을 사용해서 테이블을 갱신

### 3절. **Foreign Key 제대로 사용하기**

## 3 장 |  **데이터베이스 모델링**

---

### 1절. **데이터 모델링이란?**

### 2절. **논리적 모델링**

### 3절. **정규화**

### 4절. **물리적 모델링**

# 🍀 스터디 진행

## 📚 강의 리뷰(질문 및 정보 공유)

---

- sql 1
    
    과제 1
    SQL로 하는 데이터 분석
    SQL로 데이터를 조회하고 분석하는 방법을 배워 봅시다
    4
    데이터 분석 단계로 나아가기
    
    칼럼 자유롭게 다루기 실습
    [https://www.codeit.kr/topics/data-analysis-using-sql/lessons/3193](https://www.codeit.kr/topics/data-analysis-using-sql/lessons/3193)
    
    BETWEEN 불가능 : if 나 switch같은 순서?? 아닌듯
    실습 설명
    코드잇 피자 가게에는 피자들의 가격과 원가를 관리하는 아래와 같은 pizza_price_cost 테이블이 있습니다.
    
    id	name	price	cost
    1	Potato Bacon Pizza	22000	14000
    2	Sweet Potato Pizza	24000	14000
    3	Combination Pizza	25000	13000
    4	Bacon Cheddar Pizza	32000	20000
    5	Pineapple Pizza	25000	22000
    6	Garlic Shrimp Pizza	26000	19000
    7	Cheeze Pizza	23000	17000
    8	Pepperoni Pizza	24000	13000
    이 테이블에서 price 컬럼이 피자 가격, cost 컬럼이 피자를 만드는데 드는 비용(원가)를 나타내는데요.
    이 중에서 비용 대비 가격이 낮은, 그러니까 다른 말로 하면 효율이 떨어지는 메뉴는 각 메뉴의 원가를 절감할 수 있는 방법을 찾거나, 가격을 높이려고 합니다.
    
    원가 대비 실제 가격의 비율은 (price/cost) 로 나타낼 수 있겠죠?
    
    pizza_price_cost 테이블을 가지고 다음 작업을 해보세요.
    
    pizza_price_cost 테이블의 name, price, price/cost(원가 기준 가격의 비율) 컬럼을 조회하세요.
    
    대신 마지막 price/cost 컬럼을 사용해서 그 값이
    
    1 <= 값 < 1.5 인 경우, ‘C. 저효율 메뉴’
    1.5 <= 값 < 1.7 인 경우, ‘B. 중효율 메뉴’
    1.7 <= 값 인 경우, ‘A. 고효율 메뉴’
    라고 그 값을 변환해서 표시하는 추가적인 컬럼도 함께 조회하고 대신 이 컬럼에는 efficiency라는 alias를 붙여주세요.
    
    그리고 전체 row를 efficiency 컬럼을 기준으로 내림차순, 그 다음 기준으로 price 컬럼을 기준으로 오름차순 정렬하세요.
    
    이 중에서 가장 첫 번째 row 부터 6개만 추리세요.
    
    직접 SQL 문을 작성해서 효율이 떨어지는 메뉴들을 찾아봅시다.
    
    SELECT
    (CASE
    WHEN age = NULL THEN 'true'
    WHEN age != NULL THEN 'false'
    END) AS 'IS NULL?'
    
    FROM copang_main.member
    
    => NULL
    
    - foreign key 설정 안하고도 조인 가능한데 굳이 설정한느 이유는?

- EXISTS와 IN의 차이

먼저 말씀하신 것 처럼 EXISTS 와 IN 의 결과는 동일한게 맞습니당.
다만 EXISTS 가 IN 보다 조금 더 연산이 빠를 수 있습니다.
EXISTS 는 상관 서브쿼리에서 쓰이게 되는데, 서브쿼리의 실행 결과가 하나라도 있으면 True 를 반환합니다.

SELECT *
FROM item
WHERE EXISTS (SELECT item_id FROM review WHERE [item.id](http://item.id/) = review.item_id);

위 코드를 실행하게 되면 메인쿼리의 각 행마다 서브쿼리를 실행하게 됩니당.
즉 메인쿼리의 1행이 있다면 item 테이블 1행에서 id 를 가져와서 review 의 item_id 와 비교하게 됩니당.
그래서 만약 서브쿼리의 결과가 True 라면 그 행은 WHERE 에 의해 선택되겠죵
그리고 2행이 있다면 똑같이 item 테이블 2행에서 id 를 가져와 비교하게 되고요.
이제 차이가 있다면 아까 말씀드린 실행결과가 하나라도 있으면 True 를 반환한다는 것인데
만약 1행에서 서브쿼리를 실행할 때 item 의 id(여러개가 있겠죵?)와 review 의 item_id(review 의 첫번째 행 id)가 일치하는게 여러개가 나올 수 있다고 하더라도
서브쿼리 실행 결과 가장 먼저 만족하는 행, 즉 [item.id](http://item.id/) 와 review.item_id 가 되는 행이 발견된다면 그 뒤에 또 만족하는 행이 있더라도 바로 True 를 반환되며
다시 메인쿼리 2행에서 서브쿼리를 실행하게 될 것입니다.
반면 IN 의 경우엔 모든 행을 다 보게 되는 것이고용.
[https://choihyuunmin.tistory.com/93](https://choihyuunmin.tistory.com/93) 확인

- sql

## 📚 코드잇에서 진행한 실습 및 과제 비교

---

# 🍀 다음 스터디까지