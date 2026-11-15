---
title: "11주차-DB-RDBMS와 NOSQL"
date: 2026-09-28
updated: 2026-10-18
category: "프로그래밍 기초"
tags: ["알토르IT기초과정"]
original: https://velog.io/@xjoker7272/11%EC%A3%BC%EC%B0%A8-DB-RDBMS%EC%99%80-NOSQL
---

# Database란? 

- 일반적으로 컴퓨터 시스템에 전자 방식으로 저장된 구조화된 정보 또는 데이터의 체계적인 집합을 의미합니다.

# DBMS란?(DataBase Management System)

- 사용자와 데이터베이스 사이에서 사용자의 요구에 따라 정보를 생성해 주고 데이터베이스를 관리해 주는 소프트웨어입니다.

# SQL이란(Strucured Query Language)
- 관계형 데이터베이스 관리 시스템의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어이며 관계형 데이터베이스 관리 시스템에서 자료의 검색과 관리, 데이터베이스 스키마 생성과 수정, 데이터베이스 객체 접근 조정 관리를 위해 고안되었습니다.

# RDBMS (Relational)
- 위에서 DBMS는 사용자와 데이터베이스 사이에서 사용자의 요구에 따라 정보를 생성해주고 데이터베이스를 관리해 주는 소프트웨어라고 설명을 했습니다.
또한 기존의 RDBMS에서의 저장 방식은 SQL에 의해 저장되고 있으며 정해진 스키마에 따라 데이터를 저장하여야 합니다. RDBMS에는 DBMS앞에 R이 붙어 있습니다.
- 이 R은(Relational)의 약자로 RDBMS는 관계형 데이터베이스 관리 시스템을 의미합니다. 이름과 같이 RDBMS는 RDB를 관리하는 시스템이며 RDB는 관계형 데이터 모델을 기초로 두고 모든 데이터를 2차원 테이블 형태로 표현하는 데이터베이스입니다. 

 
- 관계형 데이터베이스(RDMBS)는 아래와와 같이 구성된 테이블이 다른 테이블들과 관계를 맺고 모여있는 집합체로 이해할 수 있습니다.

- 관계형 데이터베이스(RDMBS)에서는 이러한 관계를 나타내기 위해 외래 키(foreign key)라는 것을 사용합니다.

- 이러한 테이블간의 관계에서 외래 키를 이용한 테이블 간 Join이 가능하다는 게 RDBMS의 가장 큰 특징입니다.

# NoSQL
- NoSQL이란(Not Only SQL)의 약자로 말 그대도 위에서 설명한 RDB 형태의 관계형 데이터베이스가 아닌 다른 형태의 데이터 저장 기술을 의미하고 있습니다. 또한 NoSQL에서는 RDBMS와는 달리 테이블 간 관계를 정의하지 않습니다. 데이터 테이블은 그냥 하나의 테이블이며 테이블 간의 관계를 정의하지 않아 일반적으로 테이블 간 Join도 불가능합니다. 

 
- NoSQL은 점점 빅데이터의 등장으로 인해 데이터와 트래픽이 기하급수적으로 증가함에 따라 RDBMS에 단점인 성능을 향상시키기 위해서는 장비가 좋아야 하는 Scale-Up의 특징이 비용을 기하급수적으로 증가시키기 때문에 데이터 일관성은 포기하되 비용을 고려하여 여러 대의 데이터에 분산하여 저장하는 Scale-Out을 목표로 등장하였습니다.

 
- NoSQL을 하면 가장 유명한 Document 기반의 MongoDB를 많이 떠올리지만 MongoDB는 NoSQL한 종류로 NoSQL은 하기와 같이 다양한 형태의 저장 기술을 지원하고 있습니다.

- 이 다양한 형태의 저장기술은 RDBMS 스키마에 맞추어 데이터를 관리해야 된다는 한계를 극복하고 수평적 확장성(Scale-out)을 쉽게 할 수 있다는 장점을 가지고 있습니다.

# 쿼리 문법
## INSERT
- INSERT문의 기본 문법
테이블에 행 데이터를 입력하는 기본적인 SQL문은 INSERT입니다.

```sql 
INSERT INTO 테이블이름(열1, 열2, 열3) VALUES (값1, 값2, 값3);

```
## UPDATE
- 데이터 수정 : UPDATE
UPDATE문의 기본 문법

- UPDATE는 기존에 입력되어 있는 값을 수정하는 명령입니다.

```sql
	UPDATE 테이블이름
    SET 열1=값1, 열2=값2...
    WHERE 조건;
   ```
   
   ## DELETE
  -  데이터 삭제 : DELETE
DELETE는 행 단위로 삭제하며 형식은 아래와 같습니다.

```sql
DELETE FROM 테이블 이름 WHERE 조건;
```
- city_popul 테이블에서 New로 시작하는 도시를 삭제하기 위해 아래와 같이 실행합니다.

```sql
DELETE FROM city_popul 
    WHERE city_name LIKE 'New%';
```
    
- 만약 New로 시작하는 도시 모두를 삭제하는 것이 아니라 상위 몇 건만 삭제하려면 LIMIT 구문과 함께 사용하면 됩니다.


```sql
	DELETE FROM city_popul 
    WHERE city_name LIKE 'New%'
    LIMIT 5; #상위 5건만 삭제
 ```
 
 ## SELECT
 
- SELECT 문에서 많이 사용하는 기본 구조는 다음과 같습니다.

```sql
SELECT [컬럼명]
FROM [테이블명]
WHERE [조건]
GROUP BY [컬럼명]
ORDER BY [컬럼명] [ASC | DESC]
```
 

쉽게 설명하면, 테이블의 조건과 일치하는 데이터를 조회한다는 의미입니다.

# MongoDB 
- MongoDB는 고성능, 고가용성 및 쉬운 확장성을 제공하는 NoSQL, Document 지향 데이터베이스입니다.

- 데이터를 배열 및 중첩 Document와 같은 복잡한 데이터 유형을 효율적으로 저장할 수 있는 유연한 JSON과 유사한 형식인 BSON(Binary JSON)으로 저장합니다.

## JSON과 BSON의 차이
- JSON
-텍스트 기반.
-사람이 읽고 쓰기 쉬움.
-텍스트를 처음부터 끝까지 읽으며 분석해야 하므로 상대적으로 느림.

- BSON
-바이너리(이진법) 기반.
-기계가 읽기 쉬움(사람이 해독 매우 어려움).
-데이터 길이와 타입이 이진코드 명시되어 탐색속도 빠름.

