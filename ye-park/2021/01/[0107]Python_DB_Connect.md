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
이제 DB와 연동해보자. 샘플DB로 user 테이블을 생성하였다. <br/>
![db table](https://user-images.githubusercontent.com/55680005/103844578-80925400-50dd-11eb-90d8-2a3ed86a28b9.JPG) <br/>
Python에서 PyMySql 모듈을 import 한다.
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
Connection 객체로부터 `cursor()` 메서드를 호출하여 `Cursor`객체를 생성한다. <br/>
다양한 커서의 종류가 있지만, Python에서 데이터 분석을 주로 `pandas`로 하고 RDBMS(Relational Database System)를 주로 사용하기 때문에
데이터 분석가에게 익숙한 데이터프레임 형태로 결과를 쉽게 변환할 수 있도록 딕셔너리 형태로 결과를 반환해주는 `DictCursor`를 사용하였다.
`DictCursor`가 아닌 일반 `cursor`를 사용하면 결과가 튜플 형태로 리턴된다.
```python
 cursor = localdb.cursor(pymysql.cursors.DictCursor)
```
### Data 조작하기
DB 연결이 성공하였으면, DB 데이터를 조작해본다.<br/>
PyMySQL의 데이터 조작은 `execute()`와 `fetch()`를 사용한다.<br/>
`Cursor` 객체의 `execute()` 메서드를 사용하여 SQL 문장을 DB 서버에 보낸다.<br/>

`Cursor` 객체의 `fetchall()`, `fetchone()`, `fetchmany()` 등의 메서드를 사용하여 데이타를 서버로부터 가져온 후, `Fetch` 된 데이타를 사용한다.
```python
sql = "select * from user"
cursor.execute(sql)
result = cursor.fetchall()
```

`Connection` 객체의 `close()` 메서드를 사용하여 DB 연결을 닫는다.

