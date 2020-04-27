# 1. 기온 공공 데이터 (unit 02-01,03-01,seoul)
## 1-1. 기온데이터 분석 시작하기 
### 1. CSV 파일이란
CSV는 'Comma-Separated Values'의 약자로 각각 데이터 값을 콤마(,)로 구분하는 파일 형식을 말함.    
정부에서 운영하는 공공 데이터 포털이 제공하는 일반적인 파일 형식으로, 데이터 분석 전문가들이 자주 사용하는 파일 형식.
#### CSV 파일 특징 
1. 엑셀 프로그램에서 사용 가능
2. '메모장'과 같은 텍스트 편집기로 파일 수정 및 생성 가능 
![logo](https://blogfiles.pstatic.net/MjAyMDA0MjZfMTY5/MDAxNTg3ODY4NTg1NzM2.M334Mvlrr0fodnLpkP4CniuVDLpMWmYkNTWLHPyPuOYg.OQmSIxou1fdHYoeKBTymwCTec8M5pJCBlnxQX6F7Im0g.PNG.loveee_12/%EC%BA%A1%EC%B2%98.PNG?type=w1)

메모장으로 파일을 열면 데이터가 콤마(,)로 구분되어 있다는 것을 알 수 있다. 
#### 데이터 분석에 필요한 환경 만들기
CSV 파일 데이터 사용 하기 위해선 컴퓨터가 알아들을 수 있는 언어로 바꾸는 것이 필요-> 파이썬(python)
## 1-2. 서울 기온 데이터 분석하기
### 1. CSV파일에서 데이터 읽어오기 
CSV 모듈에는 데이터를 읽어오기 위한 reader() 함수와 데이터를 저장하기위한 writer() 함수가 있다.
- csv.reader(): CSV 파일에서 데이터를 읽어오는 함수
- csv.writer(): CSV 파일에서 데이터를 저장하는 함수
```python
import csv #csv 모듈을 불러옴 
f=open('seoul.csv','r',encoding='cp949') #csv파일을 open()로 열어 f에 저장 
data=csv.reader(f,delimiter=',') # f를 reader()함수에 넣어 data라는 csv reader 객체 생성 
print(data) #data 출력 
f.close() # 연 파일을 닫음 
```
실행값 :  <_csv.reader object at 0x0000015E5ACB0EB8>  
데이터가 csv reader 객체라는 의미. object at 뒤에 오는 것은 파일 위치.
```python
f=open('seoul.csv','r',encoding='cp949') 
data=csv.reader(f,delimiter=',')
```
seoul.csv 파일을 읽기모드(read)로 읽어오되, cp949형식(Windows 한글 인코딩 방식)으로 읽어오라는 의미이다.   
두번째 줄은 코드를 통해 읽어온 CSV 파일 데이터를 콤마(,) 기준으로 분리해서 저장하라는 의미이다. 여기서 delimiter은 구분자를 말함. 
### 2. 데이터 출력하기 
#### 데이터를 한줄 씩 출력하기 
```python
import csv 
f=open('seoul.csv',encoding='cp949')
data=csv.reader(f)
for row in data:
    print(row) # 한줄로 출력 
f.close()
```
#### 실행결과 
- 각  행의 데이터가 대괄호→ 리스트의 특성을 활용해 인덱싱과 슬라이싱을 할 수 있다. 
- 각 행의 데이터가 작은 따옴표→  각 행의 데이터가 문자열로 이루어져있음→  크기 비교시 실수 형태로 변환이 필요. 
### 3. 헤더 저장하기
헤더(header): 데이터 파일에서 여러가지 값들이 어떤 의미를 갖는지 표시한 행.   
next(): 헤더를 별도로 저장하는 함수, 첫 번째 데이터 행을 읽어오면서 데이터 탐색 위치를 다음 행으로 이동하는 명령 
```python
import csv
f=open('seoul.csv')
data=csv.reader(f)
header = next(data) #1
print(header) #2
f.close()
```
#1 : header 라는 변수에 헤더 데이터 행을 저장 
#2 : header 변수를 출력
```python
import csv
f=open('seoul.csv')
data=csv.reader(f)
header = next(data)
for row in data:
    print(row)
f.close()
```
첫번째행 다음 행이 출력됨. 
## 1-3. 서울이 가장 더웠던 날은 언제였을까?
### 1. 질문 다듬기
- 질문은 답을 찾을 수 있도록 구체적이고 명확해야한다
- 우리가 가진 데이터 만으로 질문에 대한 답을 찾을 수 있는지 확인해야한다.
### 2. 문제해결방법구상하기
1. 데이터를 읽어온다.
2. 순차적으로 최고기온을 확인한다.
3. 최고기온이 가장 높았던 날짜의 데이터를 저장한다.
4. 최종 저장된 데이터를 출력한다.
### 3. 파이썬 코드로 구현하기
#### 최고 기온을 실수로 변환
```python
import csv
f=open('seoul.csv')
data=csv.reader(f)
header = next(data)
for row in data:
    row[-1]=float(row[-1]) #1
    print(row)    
f.close()
```
#1 : 최고 기온을 실수로 변환 
#### 빈문자열 자리 채우기 
```python
import csv
f=open('seoul.csv')
data=csv.reader(f)
header = next(data)
for row in data:
    if row[-1]=='':
        row[-1]=-999
    row[-1]=float(row[-1])
    print(row)    
f.close()
```
#### 탐색과 비교의 과정 
기준이 되는 값을 설정하고, 기준값과 새로운 값을 비교한 후 기준값보다 더 큰값이 나타나면 기준값을 업데이트 한다. 그러므로 기준이 되는 값을 저장할 공간인 변수가 필요하다. 우리가 찾는 최고 기온이 가장 높은 날의 날짜와 그 날의 기온값이다. 그러므로 그 것을 저장할 변수가 필요하다.
```python
import csv
max_temp=-999 #1 최고 기온 값을 저장하는 변수
max_date='' #2 최고 기온이 가장 높았던 날짜를 저장하는 변수
f=open('seoul.csv')
data=csv.reader(f)
header = next(data)
for row in data:
    if row[-1]=='':
        row[-1]=-999
    row[-1]=float(row[-1])
    print(row)    
f.close()
```
초깃값을 -999로 꼭 지정할 필요는 없다. 
```
만약 지금까지 최고 기온 값보다 현재 행(row)의 최고 기온 값이 더 크다면 최고기온 날짜/값 업데이트. 
```
이 표현을 파이썬 코드로 옮기면,
```python
if max_temp<row[-1]:
    max_date=row[0]
    max_temp=row[-1]
```

#### 전체 코드 정리
```python
import csv #1:CSV모듈 불러오기
f=open('seoul.csv') #2:seoul.csv 파일 읽기 모드로 불러오기
data=csv.reader(f)
header = next(data) #3: 맨 윗줄을 header변수에 저장
max_temp=-999 #4: 최고기온 값저장할 변수 초기화
max_date='' #최고기온 날짜값 저장 변수 초기화
for row in data:
    if row[-1]=='': #5: 만약 데이터가 누락되었다면 최고기온을 -999로 저장
        row[-1]=-999
    row[-1]=float(row[-1]) #6: 문자열로 저장된 최고값을 실수로 변환
    if max_temp<row[-1]: #7: 만약 지금까지 최고기온보다 더 높다면 업데이트
        max_date=row[0]
        max_temp=row[-1]
f.close() #파일닫기
print('기상 관측 이래 서울의 최고 기온이 가장 높았던 날은',max_date+'로,',max_temp,'도 였습니다') #출력
```
