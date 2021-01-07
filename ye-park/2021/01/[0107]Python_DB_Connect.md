# 🔌 Python DB Connect 🔌

## 0️⃣ Python으로 DATABASE 연결하기
Python은 데이터 분석(Data Analysis)에 최적화되어 있다. <br/>
Python에서 각 DATABASE를 사용하기 위해서는 각각의 DB에 상응하는 별도의 DB모듈을 다운받아야 한다.<br/>
Python에서는 MySQL, PostgreSQL, MSSQL, Sqlite, Oracle, Sybase, Informix, mSQL 등과 같은 대표적인 DB 들이 모두 지원된다.<br/>

## 1️⃣ Python에서 MySQL 환경 구축
### PyMySQL 패키지 설치
Python에서 MySQL를 사용하기 위해 콘솔에서 라이브러리를 간단하게 설치한다. <br/>
```console
 pip install PyMySQL
```
### DB CONNECT
이제 DB와 연동해보자. 샘플 테이블로 USER를 생성하였다. <br/>
![db table](https://user-images.githubusercontent.com/55680005/103844578-80925400-50dd-11eb-90d8-2a3ed86a28b9.JPG) <br/>
Python에서 PyMySql 모듈을 `import` 한다.
```python
 import PyMySQL
```
`pymysql.connect()` 메소드를 사용하여 MySQL에 `connect()`한다. 
```python
 localdb = pymysql.connect(
    user='{user 이름}',
    passwd='{설정한 패스워드}',
    host='{host 주소}',
    db='{연결할 db 이름}',
    charset='{인코딩 설정}'
)
```
`Connection` 객체로부터 `cursor()` 메서드를 호출하여 `Cursor`객체를 생성한다. <br/>
다양한 커서의 종류가 있지만, Python에서 데이터 분석을 주로 `pandas`로 하고 RDBMS(Relational Database System)를 주로 사용하기 때문에
데이터 분석가에게 익숙한 데이터프레임 형태로 결과를 쉽게 변환할 수 있도록 딕셔너리 형태로 결과를 반환해주는 `DictCursor`를 사용하였다.
`DictCursor`가 아닌 일반 `cursor`를 사용하면 결과가 튜플 형태로 리턴된다.
```python
 cursor = localdb.cursor(pymysql.cursors.DictCursor)
```
### Data 조작하기 - 
DB 연결이 성공하였으면, DB 데이터를 조작해본다.<br/>
PyMySQL의 데이터 조작은 `execute()`와 `fetch()`를 사용한다.<br/>
`Cursor` 객체의 `execute()` 메서드를 사용하여 SQL 문장을 DB 서버에 보낸다.<br/>
#### SELECT문
`Cursor` 객체의 `fetchall()`, `fetchone()`, `fetchmany()` 등의 메서드를 사용하여 데이타를 서버로부터 가져온 후, `Fetch` 된 데이타를 사용한다.
- `fetchall()` : 모든 데이터를 한 번에 가져올 때 사용
- `fetchone()` : 한 번 호출에 하나의 행만 가져올 때 사용
- `fetchmany()` : n개만큼의 데이터를 가져올 때 사용
```python
sql = "SELECT * FROM USER"
cursor.execute(sql)
result = cursor.fetchall()
```
#### pandas 사용
`pandas`를 `import`하고 불러온 결과를 데이터프레임 형태로 만들어 더 원활하게 데이터를 조작할 수 있다.
```python
import pandas as pd
result = pd.DataFrame(result)
```
![db_pandas](https://user-images.githubusercontent.com/55680005/103905595-27104080-5142-11eb-9a03-1b994ca69073.JPG) 
#### INSERT문
user 테이블에 데이터를 삽입한다.
`execute()` 메서드를 사용해 INSERT쿼리를 실행한 후, `commit()`을 한다.
`commit()`을 하지 않으면 `execute()`를 해도 삽입하려는 데이터가 DB에 반영되지 않는다.
```python
sql = '''INSERT INTO `USER` (USER_ID, USER_NAME, CREATE_USER, CREATE_DATE) 
    VALUES ('test6', 'test6', 'admin', now());'''
cursor.execute(sql)
localdb.commit()
```
![insertdata](https://user-images.githubusercontent.com/55680005/103906453-49ef2480-5143-11eb-90a9-9ef19d2b6863.JPG)<br/>
SELECT문으로 데이터가 잘 삽입된 것을 확인할 수 있다.
#### UPDATE문
방금 삽입한 데이터를 변경해본다.
```python
sql = '''UPDATE `USER`
  SET USER_ID = 'testuser', USER_NAME = 'testuser'
  WHERE USER_NO = 7;'''
cursor.execute(sql)
localdb.commit()
```
![updatedata](https://user-images.githubusercontent.com/55680005/103906880-da2d6980-5143-11eb-93d3-4ab3135312ea.JPG)<br/>
데이터가 잘 변경되었다.
#### DELETE문
방금 삽입한 데이터를 삭제해본다. 데이터를 변경 및 삭제할 때에는 명시적으로 `Primary Key`를 `WHERE`절에 지정해주는 것이 안전하다.
```python
sql = '''DELETE FROM `USER`
  WHERE USER_NO = 7;'''
cursor.execute(sql)
localdb.commit()
# DELETE 후 확인 쿼리
# sql = "SELECT * FROM USER WHERE USER_ID = 7"
```
![deletedata](https://user-images.githubusercontent.com/55680005/103907686-efef5e80-5144-11eb-864f-b29c481cd372.JPG)<br/>
데이터가 잘 제거되었다.
사용한 `Connection` 객체의 `close()` 메서드를 사용하여 DB 연결을 닫는다.

## 🔔 Tips! 🔔
### 1. `print(rows)`
`print(rows)`문은 전체 row들을 Tuple의 Tuple로서 출력하게 되고, row[0], row[1]와 같이 인덱스를 지정하면, 첫번째, 두번째 row등을 가리키게 된다. 각 row는 Tuple로 리턴되며, 컬럼 순서대로 데이타가 표시된다.
### 2. Parameter Placeholder
실무에서는 대부분의 쿼리문에 동적으로 데이타값을 넣어야하는 경우가 많다. 동적SQL문을 작성하기 위해 파라미터값이 들어가는 위치에 `%s`(MySQL)을 넣고, `execute()` 메서드의 두번째 파라미터에 실제 파라미터값들의 Tuple을 넣어주면 된다. 문자열과 숫자 모두 `%s`를 사용하며, 문자열이라도 `%s`를 인용부호로 둘러싸지 않는다. 또, `%s`는 컬럼값을 대치할 때만 사용될 수 있다.
```python
# 한 개의 데이터 적용시, excute(SQL, a-data)
# %s을 작성한 위치대로 data를 작성하여야 올바르게 조작한다.
# SELECT 
sql = "SELECT * FROM `USER` WHERE USER_NAME = %s AND USER_ID = %s;"
cursor.execute(sql, data)
# 여러개의 데이터 적용시, executemany(SQL, multiple-data)
# 이차원 배열 혹은 이차원 튜플을 사용하여 데이터를 구성하고, 데이터 순서대로 DB에 적용된다.
# 반복문과 `execute()` 메서드를 사용하는 것보다 속도와 메모리 면에서 효율적이다.
# INSERT 
sql = "INSERT INTO `USER`(USER_NAME, USER_ID) VALUES (%s, %s);"
cursor.executemany(sql, data)
db.commit()
# 잘못된 표현
# 변수 data 안에 단일 인용부호가 있는 경우 SQL Syntax 에러를 유발시키게 된다. 
# 이러한 String Interpolation 혹은 문자열 결합을 통해 동적SQL문을 만드는 방법은 SQL Injection에 쉽게 노출되는 문제점이 있다.
data = '서\'울'
sql = "select * from customer where category=%s and region=%s" % (1, data)
curs.execute(sql)
```
### 3. Dictionary Cursor
`cursor` 생성시 `DictCursor`로 생성하면, 결과를 `Dictionary` 형태로 리턴한다. 출력 결과가 `Dictionary`이므로 row["id"], row["name"] 과 같이 컬럼명을 써서 컬럼값을 구할 수 있다. 
```python
cursor = conn.cursor(pymysql.cursors.DictCursor)
# ---생략---
rows = cursor.fetchall()
for row in rows:
  print(row)
  # 출력 : {'category': 1, 'id': 1, 'region': '서울', 'name': '김정수'}
  print(row['id'], row['name'], row['region'])
  # 1 김정수 서울
```

##### 참조 : [예제로 배우는 파이썬 프로그래밍 - Python DB API](http://pythonstudy.xyz/python/article/201-Python-DB-API)
