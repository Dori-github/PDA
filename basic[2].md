# 2. 데이터시각화 기초(unit01-02,02-02,03-02,seoul)
## 2-1. 기본 그래프 그리기
### 1. matplotlib 라이브러리란?
matplortlib 라이브러리는 파이썬에서 2D 형태에 그래프, 이미지 등을 그릴 때 사용하는 것으로, 실제 과학 컴퓨팅 분야나 인공지능 연구 분야에서도 많이 활용된다. 

#### pylot 모듈 불러오기
```python
import matplotlib.pyplot
```
pyplot: 공학용 도구로, 널리 알려진 MATLAB과 사용법이 유사함
#### pyplot 를 plt라는 별명으로 사용 
```python
import matplotlib.pyplot as plt
```
### 2. 기본 그래프 그리기 
plot() : ()에 리스트 입력, 직선/꺾은선 그래프 그릴 때 사용되는 함수
#### 그래프1
``` python
import matplotlib.pyplot as plt 
plt.plot([10, 20, 30, 40])
plt.show()
```
plt.plot()는 matplotlib.pyplot.plot()와 같은 명령이다. 

![logo](https://blogfiles.pstatic.net/MjAyMDA0MjZfNTIg/MDAxNTg3ODcxNzIyNzQw.D55fcv7_q6ziYT04zoohOFqFCFh-7U4mDZwKc5ybL9kg.OlGrwAlpwiiZl3OmA7mGeBu4mvjn-ArByexAWix4TBYg.PNG.loveee_12/%EC%BA%A1%EC%B2%982.PNG?type=w1)  

plot() 함수에 입력된 리스트는 y축의 값으로 입력되며, x축 값은 자동으로 0부터 1까지 증가하는 정수로 입력된다.
x축의 값을 생략할 경우 range(y축 데이터 개수)로 표현 가능.

#### 그래프2
```python
import matplotlib.pyplot as plt
plt.plot([1,2,3,4],[12,43,25,15])
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjYy/MDAxNTg4MDQ0MTkxMzk4.iCXgEzEy60DjH-3R8cpLw2pPSHXAm1G7_zrZtJl48YUg.G4LenRIhA7lOLpraJt3GgmVclDgPvGRinonyaW7C5jAg.PNG.loveee_12/%EC%BA%A13.png?type=w1)  
plot() 함수에 입력된 첫번째 리스트가 x축 값이고, 두번째 리스트가 y축값이다. 

#### plot함수에 기본 그래프 그리기
1. import matplotlib.pyplot as plt : 라이브러리 불러오기
2. plt.plot([x축데이터],[y축데이터]) : plot()함수에 데이터 입력하기
3. plt.show() : 그래프 보여주기

### 3. 그래프에 옵션 추가하기
#### 그래프에 제목넣기 
title() : 제목을 넣는 함수
plot.title('제목을 넣을 문자열')
```python
import matplotlib.pyplot as plt
plt.title('plotting')
plt.plot([10,20,30,40])
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMTQy/MDAxNTg4MDQ0MTkxNzI3.oaFpX1Wi0Q9HYSn8QC1033lGSVgVICf85yfL2aYUR9Eg.B9z2etWq9JPBF2_SeXbjhiKISMPA0EvEQhLz17HGsg8g.PNG.loveee_12/%EC%BA%A14.png?type=w1)  
#### 그래프에 범례넣기
범례 : 그래프가 의미하는 바를 구별 할 수 있는 것
보통 두개 이상의 데이터를 표시할 때 사용함. 
```python
import matplotlib.pyplot as plt
plt.title('legend')
plt.plot([10,20,30,40],label='asc') #1: 증가를 의미하는 asc 범례
plt.plot([40,30,20,10],label='desc') #2: 감소를 의미하는 desc 범례
plt.legend()
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjgx/MDAxNTg4MDQ0MTkxOTg5.PtIEX19GthqQzY8AX9-ryutemgaZfcPrdMwt9CJn7Pwg.DLlZs6fRsSdnk4_q36U6BN_7SeQhijxB7SCd8J1y6TUg.PNG.loveee_12/%EC%BA%A15.png?type=w1)  
plot 함수에 label 이라는 속성의 레이블 값으로 원하는 문자열을 넣어주고, 그래프 그리기 전에 legend()함수를 실행시키면 테이블 값이 범례로 나타난다. 
#### 범례 위치지정 
```python
plot.legend(loc=5)
``` 
loc에 들어가는 숫자는 1-10 까지 가능.
|2| 9 |1|
|-|-|-|
| 6 | 10 |5,7
|3|8|4

#### 그래프 색상 바꾸기
원하는 색상으로 바꾸려면 color 속성을 추가하면 된다.
```python
import matplotlib.pyplot as plt 
plt.title('color') #제목설정 
#그래프그리기
plt.plot([10,20,30,40],color='skyblue',label='skyblue')
plt.plot([40,30,20,10],'pink',label='pink')
plt.legend()
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMzMg/MDAxNTg4MDQ0MTkyMzA0.TpvgwIl5FjEzSQ-BZtJXJdqxNlyG4CuzWI2UcoRNu0sg.-cTwDhwzzN4QBkNQEjZ1SmzlgBT3ej1KLJCUl669SAgg.PNG.loveee_12/%EC%BA%A16.png?type=w1)  
#### 그래프 선모양 바꾸기
그래프 선모양을 다양한 형태로 바꾸고 싶을 때는 linestyle 속성에 원하는 모양을 지정하면 된다. linestyle 속성 대신 ls 라고 작성 할 수 있다. 
```python
import matplotlib.pyplot as plt
plt.title('linestyle') #제목설정
#빨간색 dashed 그래프
plt.plot([10,20,30,40],color='r',linestyle='--',label='dashed')
#초록색 dashed 그래프
plt.plot([40,30,20,10],color='g',ls=':',label='dotted')
plt.legend #범례표시
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjQw/MDAxNTg4MDQ0MTkyNjEw.q1IFwkrZ2IFkx0VhB2Vp5KW5dMIoH6sloHxIfwr2k7og.lYVcbKbnv4US_Y_nlM2EupKR3QxHmuY_-JrNW4qOjnsg.PNG.loveee_12/%EC%BA%A17.png?type=w1)  
#### 마커모양 바꾸기 
plot 함수에 marker 속성 설정 : 점 형태 그래프 
이때 색상과 마커 모양을 한번에 설정 할 수도 있다. 
- 'r.' 의 마침표(.)는 점모양을 의미  
- 'g^'의 ^는 삼각형 모양을 의미
```python
import matplotlib.pyplot as plt
plt.title('marker') #제목설정
plt.plot([10,20,30,40],'r.',label='circle') #빨간색 원형 마커 그래프
plt.plot([40,30,20,10],'g^',label='triangle=up') #초록색 삼각형 마커 그래프
plt.legend #범례표시
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMTU1/MDAxNTg4MDQ0MTkyODk4.JMvT_piBJYgIZsqt7kD3UvQ7_QTxvBmSstYD5Wz40lwg.fjOwwCshJV2GojzWvyli7pEDL4gqOVWaB_2NPHDBoxsg.PNG.loveee_12/%EC%BA%A18.png?type=w1)  
색/선/마커 모양 동시 설정 : '<색상><마커모양><선모양>' 순으로 코드 작성 
ex) plt.plot([1,2,3,4],]'r.--')
## 2-2. 내 생일의 기온변화를 그래프로 그리기 
### 1. 데이터에 질문하기
#### 데이터 읽어오기
```python
import csv
f=open('seoul.csv')
data=csv.reader(f)
for row in data:
    print(row)
```
#### 최고기온 데이터만 출력 
next()함수를 이용해 헤더 부분을 제거.
```python
import csv
f=open('seoul.csv')
data=csv.reader(f)
next(data)
for row in data:
    print(row[-1])
```
row[0]은 날짜, row[2]는 평균기온, row[3]은 최저기온, row[4]는 최고 기온을 의미.
####  데이터 리스트에 저장하기
result 리스트를 생성하여 최고기온 데이터를 날짜 순으로 저장.
```python
import csv
f=open('seoul.csv')
data=csv.reader(f)
next(data)
result=[] #최고기온 데이터를 저장할 리스트 생성
for row in data:
    if row[-1] !='': #최고 기온 데이터 값이 존재한다면
        result.append(float(row[-1])) # result 리스트에 최고 기온값 추가
print(result)
#print(len(result)) 데이터 개수 확인
```
### 2. 데이터 시각화하기
```python
import csv 
import matplotlib.pyplot as plt 
f=open('seoul.csv')
data=csv.reader(f)
next(data)
result=[] 
for row in data:
    if row[-1] !='': 
        result.append(float(row[-1])) 
plt.plot(result,'r') #result 리스트에 저장된 값을 빨간색 그래프로 그리기
plt.show() #그래프나타내기
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMTA1/MDAxNTg4MDUxMDg5MDgx.WFSMVMP0LEHiLcqULTm1vp3HfPerhly1V9FTsgE1Djkg._F73OEnvxsIMxTaYReAuk4-cd7uUc9Pog4NYnpKzjDIg.PNG.loveee_12/%EC%BA%A19.png?type=w1)  
figure() : figsize 속성 값을 변경하여 그래프 크기 조절
figsize=(가로길이, 세로길이) 형식으로 속성 지정. 
ex) plt.figure(figsize=(10,2)) 가로로 10인치, 세로로 2인치

### 3. 날짜 데이터 추출하기
splt() : 사용자가 설정하는 특정 문자 기준으로 문자열 분리
```python
s='hello python'
print(s.split())
```
특정 문자가 없다면 해당 문자를 기준으로 문자열을 분리
```python
date='1907-10-01'
print(date.split('-'))
```
실행결과 : ['1907', '10', '01']

여기에 리스트 인덱싱 기능을 활용 하면 날짜 연,월,일 각각 추출 가능.
```python
date='1907-10-01'
print(date.split('-')[0])
print(date.split('-')[1])
print(date.split('-')[2])
```
실행결과 
1907 
10 
01
#### split 함수를 이용하여 8월 최고기온 데이터 그래프 그리기
```python
import csv
f=open('seoul.csv')
data =csv.reader(f)
next(data)
result=[]
for row in data:
    if row[-1]!='': #1:최고기온 값이 존재한다면
        if row [0].split('-')[1]=='08': #2:8월에 해당하는 값이라면
            result.append(float(row[-1])) #3:result 리스트에 최고 기온 값추가
plt.plot(result,'hotpink') #result에 저장된 값을 hotpink 색으로 그리기
plt.show()  #그래프나타내기
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMTky/MDAxNTg4MDUxMDg5Mzcw.gL02-QuYF1XSdwpJrjJmsI1H1i7LhiNrgbEQBHvEuGMg.j9eerzQeOnZl6YIlYlrZ2mnbGwX_wV3NdgB9VlNletcg.PNG.loveee_12/%EC%BA%A110.png?type=w1)  
매년 돌아오는 생일 기준으로 그래프 그리기
```python
import csv
f=open('seoul.csv')
data =csv.reader(f)
next(data)
result=[]
for row in data:
    if row[-1]!='': 
        if row [0].split('-')[1]=='09'and row[0].split('-')[2]=='03':
            result.append(float(row[-1])) 
plt.plot(result,'hotpink') 
plt.show()  
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjcg/MDAxNTg4MDUxMDg5NjMx.yj58wHLfT6wTMdJA0-sobtlN4KsdOkebcNHybpQyp0Eg.-IOoNLapPswwuuXk66XRh0s7mlUZpEAQRkmeyYwGduMg.PNG.loveee_12/%EC%BA%A111.png?type=w1)  
1983년 이후 2월 14일의 최고기온과 최저기온을 추출한 그래프 그리기
```python
import csv
import matplotlib.pyplot as plt
f=open('seoul.csv')
data =csv.reader(f)
next(data)
high=[] #1:최고기온 값을 저장할 리스트 high 생성
low=[] #2:최저기온 값을 저장할 리스트 low 생성 
for row in data:
    if row[-1]!='' and row[-2]!='': #3:최고기온값과 최저기온값이 존재한다면
        if 1983<=int(row[0].split('-')[0]): #4:1983년 이후 데이터라면
            if row[0].split('-')[1]=='02'and row[0].split('-')[2]=='14': #5:2월14일이라면
                high.append(float(row[-1])) #6:최고기온 값을 high 리스트에 저장
                low.append(float(row[-2])) #7:최저기온 값을 low 리스트에 저장
plt.plot(high,'hotpink') #8:high리스트에 저장된 값을 hotpink 색으로 그리기
plt.plot(low,'skyblue') #9:low리스트에 저장된 값을 skyblue색으로 그리기
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjgw/MDAxNTg4MDUxMDkwMjE4.ln2T5gcK_NYjHuUrr_YsCCOqalnuj8mElp_cmNGSMpAg.kHA6f6-P7DnKO2qutcoARquN06xxLaUb3VHNRq60Pewg.PNG.loveee_12/%EC%BA%A112.png?type=w1)  
기존 그래프에 제목과 한글폰트 설정하기
```python
import csv
import matplotlib.pyplot as plt
f=open('seoul.csv')
data =csv.reader(f)
next(data)
high=[] 
low=[] 
for row in data:
    if row[-1]!='' and row[-2]!='': 
        if 1983<=int(row[0].split('-')[0]): 
            if row[0].split('-')[1]=='02'and row[0].split('-')[2]=='14': 
                high.append(float(row[-1])) 
                low.append(float(row[-2])) 
plt.rc('font',family='Malgun Gothic')  #폰트추가
plt.title('내 생일의 기온 변화 그래프') #제목추가
plt.plot(high,'hotpink') 
plt.plot(low,'skyblue') 
plt.rcParams['axes.unicode_minus']=False #-추가
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfNzAg/MDAxNTg4MDUxMDkwNDg1.IpFfrSAitgJ2cU1lrX5rjUrmAp2wkYN8Sq14xja_RTQg.uGyIjhe86NKlUPr2sFFU883i7UX0i_xYWjdFAEkPfOgg.PNG.loveee_12/%EC%BA%A113.png?type=w1)    
#### 내 생일 기온 변화를 그래프로 시각화하기 
```python
import csv
import matplotlib.pyplot as plt
f=open('seoul.csv')
data =csv.reader(f)
next(data)
high=[]  #최고기온 값을 저장할 리스트 high 생성
low=[]  #최저기온 값을 저장할 리스트 low 생성
for row in data:
    if row[-1]!='' and row[-2]!='': #최고기온값과 최저기온 값이 존재한다면 
        date=row[0].split('-') #날짜값을 -문자 기준으로 구분하여 저장
        if 1983<=int(date[0]): #1983년 이후 데이터라면
            if row[0].split('-')[1]=='02'and row[0].split('-')[2]=='14': #2월14일이라면
                high.append(float(row[-1]))  #최고기온값을 high리스트에 저장
                low.append(float(row[-2])) #최저기온값을 low리스트에 저장
plt.rc('font',family='Malgun Gothic')  #맑은 고딕을 기본글꼴로 설정
plt.title('내 생일의 기온 변화 그래프') #제목추가
plt.rcParams['axes.unicode_minus']=False #마이너스 기호 깨짐 방지
# 리스트에 저장 된 값을 색으로 그리고 레이블표시
plt.plot(high,'hotpink',label='high') 
plt.plot(low,'skyblue',label='low') 
plt.legend() #범례표시
plt.show() #그래프나타내기
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMTE5/MDAxNTg4MDUxMDkwNzUw.OP0ebJY54AwGpLjXnlpfxur34VJ6nlNPMG9N93nRpyMg.nyljMGt_elqV2pFRgZtKkpTooDOJtoHvNMK4DuaDFZ8g.PNG.loveee_12/%EC%BA%A114.png?type=w1)  
## 2-3. 기온데이터를 다양하게 시각화하기
### 1. 히스토그램 
#### hist함수 
히스토그램 : 자료 분포 상태를 막대그래프로 나타낸것  
hist() : 히스토그램을 그리기 위한 함수  
plot() : 꺾은선 그래프를 그리기 위한 함수 
```python
import matplotlib.pyplot as plt
plt.hist([1,2,3,4,5,6,6,7,8,10])
plt.show
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjMx/MDAxNTg4MDcwMDI2NjEx.dWRq9cIhb9YK2Ne1sT87JxFJs3ibUWiSPW1wrsFSDN8g.dehXA3py2ihxhd6rpGTdNg1juK1ExtrBReAs4V8PUxkg.PNG.loveee_12/%EC%BA%A11.png?type=w1)  
### 2. 주사위시뮬레이션 
#### 주사위시뮬레이션 과정 
1. 주사위를 굴린다.
2. 나온 결과를 기록한다.
3. 1-2번 과정을 n번 반복한다.
4. 주사위의 눈이 나온 횟수를 히스토그램으로 그린다.

####  random모듈의 randint() 함수를 사용해보기. 
```python
import random 
print(random.randint(1,6))
```
실행결과 : 1-6숫자 중 하나가 무작위로 출력된다. 
#### 주사위 굴리는 것을 시뮬레이션 해보기   
주사위를 여러번 굴리는 상황을 시뮬레이션 하기 위해 for반복문을 사용하고, 랜덤 숫자는 dice라는 이름의 리스트 순서대로 저장한다.
```python
import random
dice=[]
for i in range(5):
    dice.append(random.randint(1,6))
print(dice)
```
#### 이 dice 리스트를 히스토그램으로 표현하기.
```python
import matplotlib.pyplot as plt 
dice=[]
for i in range(5):
    dice.append(random.randint(1,6))
plt.hist(dice,bins=6)
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjI5/MDAxNTg4MDcwMDI2OTE1.wLL5Tb1Hiram7Kt_IKJI0cekh66V3ZcMvm-TIpGPvdAg.krPeqQVmSQPha0V7XMkX54zfkHjdprLMT3RnlkkjxMcg.PNG.loveee_12/%EC%BA%A12.png?type=w1)  
여기서 bins 옵션은 가로축의 구간 개수를 설정하는 속성이다. dice 리스트에 저장 된 값 빈도에 따라 막대의 값이 달라진다. 
### 3. 기온 데이터를 히스토그램으로 표현하기
 모든 최고 기온 데이터를 추출하여 히스토그램으로 표현. 색은 빨간 색으로, 구간은 100으로 설정.
```python
import csv
import matplotlib.pyplot as plt
f=open('seoul.csv')
data=csv.reader(f)
next(data)
result=[]
for row in data:
    if row[-1]!='':
        result.append(float(row[-1]))
plt.hist(result,bins=100,color='r') #히스토그램으로 나타내기
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMTk1/MDAxNTg4MDcwMDI3MjA2.zhgFNtsLuZ-hvFceGdMpDAdRTMbOCiHvKBot2ExsaBYg.jTUrReW03YUE7xC1r3FSjZkYJbTtnht7Ty5430u2nwsg.PNG.loveee_12/%EC%BA%A13.png?type=w1)  
#### 8월 기온 데이터를 히스토그램으로 표현하기 
```python
import csv
import matplotlib.pyplot as plt
f=open('seoul.csv')
data=csv.reader(f)
next(data)
aug=[] #1: 8월의 최고 기온 값을 저장할 aug리스트 생성 
for row in data:
    month=row[0].split('-')[1] #2:-로 구분된 값 중 2번째 값을 month에 저장
    if row[-1]!='':
        if month =='08':  #3:8월달이라면 
            aug.append(float(row[-1])) #4:aug리스트에 최고기온 값 추가
plt.hist(aug,bins=100,color='r')
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjgw/MDAxNTg4MDcwMDI3NDcy.wpsML_GJtYZ0zk0eshGPbkdyhIPvKkPHVU7K3_ULjeQg.A_DrfbCqNnzZmwNJG2J1zkvBDS1KyJXym56yEwXrQg8g.PNG.loveee_12/%EC%BA%A14.png?type=w1)
#### 1월과 8월의 데이터를 히스토그램으로 시각화하기
```python
import csv
import matplotlib.pyplot as plt
f=open('seoul.csv')
data=csv.reader(f)
next(data)
aug=[] #1: 8월의 최고 기온 값을 저장할 aug리스트 생성 
for row in data:
    month=row[0].split('-')[1] #2:-로 구분된 값 중 2번째 값을 monthdp wjwkd 
    if row[-1]!='':
        if month =='08':  #3:8월달이라면 
            aug.append(float(row[-1])) #4:aug리스트에 최고기온 값 추가
plt.hist(aug,bins=100,color='r')
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjcz/MDAxNTg4MDcwMDI3NzI3.MxcCkHGPf2TICdZ7OwQ8Kufji2r6J85F69FmWTBi9Dwg.tjNeo9jcDRYpU42nlb0nTfPWeemCwXUE5uvkYqzIrIkg.PNG.loveee_12/%EC%BA%A15.png?type=w1)  
### 4. 기온 데이터를 상자 그림으로 표현하기 
상자그림: 자료에서 얻어낸 최댓값, 최솟값, 상위1/4, 2/4(중앙),3/4에 위치한 값을 보여주는 그래프를 말함.   

#### randint()함수를 사용하여 임의의 데이터를 만들고, 그 데이터를 상자 그림으로 나타내보자.  
 (이때 범위는 1-1000으로 설정)  
```python
import matplotlib.pyplot as plt
import random
result=[]
for i in range(13):
    result.append(random.randint(1,1000))
print(sorted(result))
plt.boxplot(result)
plt.show()
```
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfNTUg/MDAxNTg4MDcwMDI3OTk1.9kV79v2_Rh48ux-f4nOGelGCDaNS5pWEV3KxCR5Abewg.aH8Q81grNd5BHJFY4IR0JHr_qR-tKaL_TSlwy4FJjHIg.PNG.loveee_12/%EC%BA%A16.PNG?type=w1)  
#### 다른 위치 값이 알고싶다면?
```python
import matplotlib.pyplot as plt
import random
result=[]
for i in range(13):
    result.append(random.randint(1,1000))
plt.boxplot(result)
plt.show()
import numpy as np
print(sorted(result))
# 1/4,2/4,3/4 정확한 위치값 알아내기 
result=np.array(result)
print("1/4:"+str(np.percentile(result,25)))
print("2/4:"+str(np.percentile(result,50)))
print("3/4:"+str(np.percentile(result,75)))
```
#### 서울 최고 기온 데이터를 상자그림으로 표현하기 
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjkz/MDAxNTg4MDcwMDI4Mjgw.jnwtKq1e7pr6jk9U6v2bLx1rBYqgbi2jID1YN_WRycYg.xuoDzCw9dczqy4SRberAqVBKdYhHlF7hicLo9a3b91kg.PNG.loveee_12/%EC%BA%A17.png?type=w1)  
```python
import csv 
f=open('seoul.csv')
data=csv.reader(f)
next(data)
result=[]

for row in data:
    if row[-1]!='':
        result.append(float(row[-1]))
import matplotlib.pyplot as plt
plt.boxplot(result) #상자그림으로 나타내기 
plt.show()
```
#### 1월과 8월 상자그림 그려보기 
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMTk5/MDAxNTg4MDcwMDI4NTU5.ZvmQa7xyJ9BeDTcx9PTqOcL0V9OA1PBzQfvMl3x3_cgg.RBuf4p0lbY5QaYtYtOCoAssvaFsiZ8xuAknte7QJLasg.PNG.loveee_12/%EC%BA%A18.png?type=w1)  
```python
import csv 
f=open('seoul.csv')
data=csv.reader(f)
next(data)
result=[]

for row in data:
    if row[-1]!='':
        result.append(float(row[-1]))
import matplotlib.pyplot as plt
plt.boxplot(result) #상자그림으로 나타내기 
plt.show()
```
위 아래 그려진 동그라미는 이상치 값을 표현한 것으로, 다른 수치에 비해 너무 크거나 작은 값을 자동으로 나타낸 값이다. 

#### 8월 최고 기온 데이터와 1월의 최고 기온 데이터를 원소로 하는 리스트 
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfMjIx/MDAxNTg4MDcwMDI4ODQ0.P_GzhYTMCJWhtdQ3x4JXMorG3LgqN6xIvC1Kf0lI218g.y6bIYpKDsQSNCi80ZVijKOMIfe4BmRTrfS5e58kjlNQg.PNG.loveee_12/%EC%BA%A19.png?type=w1)  
```python
import csv 
f=open('seoul.csv')
data=csv.reader(f)
next(data)
result=[]

for row in data:
    if row[-1]!='':
        result.append(float(row[-1]))
import matplotlib.pyplot as plt
plt.boxplot([aug,jan]) 
plt.show()
```
#### 최고 기온 데이터를 월별로 구분하여 표현하기 
1. 데이터를 월별로 분류해 저장한다.
2. 월별 데이터를 상자 그림으로 그려본다.  
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfNiAg/MDAxNTg4MDcwMDI5MTgx.32Up3LMbOfkJ__wb7RsofFikVJwbZctQqgwLvHd6btQg.6mjd-7tW5sYtrkxkKs16bjTEdl-98txM3YeD4u72oUcg.PNG.loveee_12/%EC%BA%A110.png?type=w1)  
```python
import matplotlib.pyplot as plt
import csv 
f=open('seoul.csv')
data=csv.reader(f)
next(data)
# 월별 데이터를 저장할 리스트 month 생성하기
month=[[],[],[],[],[],[],[],[],[],[],[],[]]

for row in data:
    if row[-1]!='':
        #월과 같은 번호의 인덱스에 월별 데이터 저장
        month[int(row[0].split('-')[1])-1].append(float(row[-1]))
plt.boxplot(month)
plt.show()
```
#### 코드과정
1. 1월부터 12월 까지의 데이터를 분류하기 위해 빈 리스트 12개 생성
2. 날짜에서 추출한 월 별 데이터를 정수로 변환한 1-12 사이의 숫자에서 1을 뺀값인 0-11까지의 인덱스 값에 월별 데이터를 저장.
#### 8월 일별 기온 데이터를 상자 그림으로 표현하기
![](https://blogfiles.pstatic.net/MjAyMDA0MjhfOTIg/MDAxNTg4MDcwMDI5NzE5.7occFL4ex5WFsbZdR1WRXtMOpmFGk0n1ZPLf6DyD5aMg.9FCnmi-0BuvMq9yJfCRlVivqGfiebEGUa91zvA6d-QUg.PNG.loveee_12/%EC%BA%A111.png?type=w1)  
```python
import matplotlib.pyplot as plt
import csv
f=open('seoul.csv')
data=csv.reader(f)
next(data)
day=[] #1:일별 데이터를 저장할 리스트 day생성
for i in range(31):
    day.append([]) #2: day리스트 내 31개 리스트 생성 
for row in data:
    if row[-1]!='':
        if row[0].split('-')[1]=='08': #8월이라면
            #최고 기온 값저장 
            day[int(row[0].split('-')[2])-1].append(float(row[-1]))
plt.style.use('ggplot') #3:그래프 스타일 지정
plt.figure(figsize=(10,5),dpi=300) #4:그래프 크기 수정
plt.boxplot(day,showfliers=False) #5:아웃라이어 값 생략 
plt.show()
 ```
