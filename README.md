# 주피터 노트북(jupyter notebook)
<details>
<summary>접기/펼치기</summary>
<br>

대화형 컴퓨팅 환경을 제공하는 오픈소스 웹 응용 프로그램이다.  
셀 단위로 실행할 수 있는 편집 프로그램이다.  
데이터를 각 셀마다 확인할 수 있어 개발할 때 굉장히 편리하다.  
즉시 실행할 수 있어, 데이터 분석 및 머신러닝 실험, 프로토타이빙 등에 사용된다.  

원래는 웹브라우저에 띄운 후 다른 프로그램에서 사용을 해야 하지만, 
vscode을 사용할 경우 확장 프로그램으로 바로 사용이 가능하다.
.ipynb 확장자로 파일을 만들면 vscode에서 자동으로 인식된다.

실행 명령은 `Ctrl + F5` 이며 `Shift + F5`로 실행시 다음 셀을 만들면서 실행하게 된다.

한개의 주피터노트북 파일은 하나의 커널로써 동일한 메모리공간(네임스페이스)을 공유한다.  
이는 한개의 주피터노트북 파일 내에서 여러 쉘들이 서로 변수나 함수등을 공유할 수 있다.  
이를 공유 실행 환경 이라고 한다.  
유의할점은, 변수나 함수를 정의한 후 실행하지 않으면 다른 쉘에서 해당 변수나 함수에 접근이 불가능하다는 점이다.  

주피터 노트북은 python 실행기와 다르게 대화형 인터프리터로 동작하기 때문에,  
마지막 표현식의 평가 결과를 자동으로 출력해주는 특징이 있다.  
- 리터럴
  ```py
  10 # 10 출력
  ```
- 변수
  ```py
  var = 20 # 20 출력
  ```
- 함수
  ```py
  def func(): return 30
  func() # 30 출력
  ```

</details>
<hr>
<br>


# print() - 여러 인수 출력
<details>
<summary>접기/펼치기</summary>
<br>

print() 함수에서 쉼표를 구분으로 문자열 혹은 변수 여러개를 매개변수로 전달할 경우, 띄어쓰기 1칸이 포함되어 다중으로 출력된다.

```py
print("메롱","약오르지","까꿍")
```

```text/plain
메롱 약오르지 까꿍
```
</details>
<hr>
<br>

# 출력 포맷 f-string
<details>
<summary>접기/펼치기</summary>
<br>

문자열과 변수를 합쳐서 새로운 문자열을 만들고 싶을 때 사용한다.  
자바스크립트에서 백틱 표현식(템플릿 리터럴)과 유사하다.

문자열 따옴표 혹은 쌍따옴표 앞에 f 키워드를 붙힌 후 문자열 내에 중괄호 안에 변수를 넣어 `f"메롱 {변수} 까꿍"` 형태로 사용한다.

```py
value = "약오르지"
print(f"메롱 {value} 까꿍")
```

</details>
<hr>
<br>

# for문 유의사항 (range와 지역변수)
<details>
<summary>접기/펼치기</summary>
<br>

`for i in range(a):` 와 같이 range의 인수가 1개인 경우  
i의 값은 순차적으로 0부터 시작해서 a-1만큼 할당된다.  
이때 i는 지역변수이므로 for문 선언 전 외부에서 `i = 1`을 하더라도 0부터 시작하게 된다.

```py
i = 3
for i in range(10):
  print(i)
```
</details>
<hr>
<br>

# 자료구조
대량의 데이터를 효율적으로 관리할 수 있는 데이터의 구조

- 파이썬의 자료구조 종류
  - 리스트
  - 튜플
  - 딕셔너리

## 리스트
<details>
<summary>접기/펼치기</summary>
<br>

여러개의 데이터를 저장할 수 있는 자료형
 동적으로 새로운 데이터를 추가하거나 변경할 수 있다.  
`변수 = [a, b, c]`와 같이 대괄호로 여러개의 데이터를 감싼다.

```py
list = [1, 2, "3"]
```

### 인덱싱(데이터 접근)
리스트 내 특정 위치의 데이터에 접근할때 `el = 변수명[0]` 형태로 인덱스 번호를 통해 접근한다.
```py
list = [1, 2, "3"]

el0 = list[0] # 1
el1 = list[1] # 2
el2 = list[2] # "3"
print(el0, el1, el2) # 1, 2, "3"
```

### 데이터 할당
인덱싱을 통해 데이터에 접근하여 데이터를 할당할 수 있다.
```py
list = [1, 2, "3"]
list[0] = 4
list[1] = "5"
list[2] = 6
print(list) # 4, "5", 6
```

### 데이터 추가
append() 함수를 통해 리스트 마지막에 요소를 추가할 수 있다.  

```py
list.append(7)
print(list) # [4, "5", 6, 7]
```

### 데이터 삭제
`del` 키워드를 사용하여 `del list[0]` 형태로 원하는 인덱스의 요소를 제거할 수 있다.  
```py
del list[1]
print(list) # [4, 6, 7]
```

### 리스트 길이
builtin 내장함수인 len()함수를 통해 리스트의 길이를 알 수 있다.  
```py
len(list) # 3
```

### 슬라이싱(자르기)
```py
list = [1, 2, 3, 4, 5, 6, 7, 8]
list[0:2] # [1, 2]: 인덱스 0 부터 2의 앞까지
list[:2] # [1, 2]: 첫번째 0은 생략 가능
list[1:4] # [2, 3, 4]: 인덱스 1부터 3까지
list[3:8] # [4, 5, 6, 7, 8]: 인덱스 3부터 7까지
list[3:] # [4, 5, 6, 7, 8]: 마지막 인덱스 생략 가능
list[::2] # [1, 3, 5, 7]: 3번째는 step 즉, 2일경우 2단계씩 건너뜀 - 0, 2, 4, 6 인덱스
```

### 리스트와 반복문
리스트와 반복문을 결합하여 사용할 수 있다.  
`for 변수 in [리스트]:` 형태로 사용한다.  
리스트는 순서가 있는 자료형인 순서열이기 때문에 for문의 in절 뒤에 들어갈 수 있다.  

```py
inventory = ["대검", "포션", "마법사"]
for item in inventory:
  print(item + "을(를) 확인했습니다.")
  print("창닫기")
```

### 2차원 리스트

`[[a,b,c], [d,e,f], [g,h,i]]` 형태와 같이 리스트 안에 리스트가 들어있는 구조이다.

```py
game_map = [
  ["대검", "포션", None], # None: 아무것도 없는 자료형
  [None, "보물상자", "포션"],
  ["몬스터", None, "열쇠"],
]
game_map[0] # ['대검', '포션', None]
game_map[0][2] # None은 아무것도 출력되지 않음
type(game_map[0][2]) # NoneType
game_map[1][2] # 포션
```
</details>
<hr>
<br>

## 튜플
<details>
<summary>접기/펼치기</summary>
<br>

순서가 있는 요소들의 모음으로 새로운 데이터를 추가하거나 변경할 수 없이 고정되는 특징이 있다.  
리스트와 같이 여러 데이터를 저장할 수 있으나, 리스트와 다르게 추가/삭제 등 수정이 불가능하다.  
`변수 = (a, b, c)`와 같이 소괄호로 여러개의 데이터를 감싼다.  

### 특징
- **데이터 보호:** 실수로 데이터가 변경될 위험을 방지할 수 있다.
- **성능:** 리스트에 비해 더 적은 메모리를 사용하고 속도가 빠르다.

```py
leg_day = ("스쿼트", "런지", "레그컬")
print(leg_day) # ('스쿼트', '런지', '레그컬')
```

### 데이터 조작:변경 - 오류
```py
leg_day[0] = "벤치프레스" # TypeError: 'tuple' object does not support item assignment (tuple 객체는 아이템 할당을 제공하지 않는다)
```

### 데이터 조작:추가 - 오류
```py
leg_day.append("숄더프레스") # AttributeError: 'tuple' object has no attribute 'append' (tuple 객체는 append 속성이 없음)
```
### 데이터 조작:삽입 - 오류
```py
del leg_day[0] # TypeError: 'tuple' object doesn't support item deletion (tuple 객체는 삭제를 제공하지 않는다.)
```

</details>
<hr>
<br>

## 딕셔너리
<details>
<summary>접기/펼치기</summary>
<br>

키(key)와 값(value)를 쌍(pair)으로 가지는 사전형태의 자료형이다.  
`변수 = {'key': value, 'key': value}` 와 같이 {} 중괄호 형태로 key:value 쌍의 데이터들을 감싼다.

### 딕셔너리 순회 함수
- 변수.keys(): 딕셔너리의 모든 key를 가져온다.  
- 변수.values(): 딕셔너리의 모든 value를 가져온다.  
- 변수.items(): 딕셔너리의 모든 key와 value를 가져온다.  

```py
stock_prices = {
  "삼성전자": 81000,
  "SK하이닉스": 140000,
  "네이버": 35000
}
print(stock_prices) # {'삼성전자': 81000, 'SK하이닉스': 140000, '네이버': 35000}
```

### 속성 접근(key)
```py
print(stock_prices['삼성전자']) # 81000
print(stock_prices['네이버']) # 35000
print(stock_prices['스타트코딩']) # 35000
```

### keys()- key 목록 순회
```py
for key in stock_prices.keys():
  print(key)

```
### values()- value 목록 순회
```py
for value in stock_prices.values():
  print(value)
```

### items()- item 목록 순회
```py
for item in stock_prices.items():
  print(item)
```

#### items와 언패킹
```py
for key, value in stock_prices.items():
  print(key, value)
```
앞서 items()를 통해 순회한 item은 `(key, value)`과 같이 튜플 형태로 추출된다.
리스트와 튜플 모두 파이썬에서는 언패킹 문법을 지원한다.  
언패킹에 의해 튜플의 2 값을 각각 변수로 추출할 수 있다.

```py
# 언패킹 - 리스트
key, value = ['삼성전자', 81000]
print(key) # '삼성전자'
print(value) # 81000

# 언패킹 - 튜플
key, value = ('삼성전자', 81000)
print(key) # '삼성전자'
print(value) # 81000

# 언패킹 - 튜플(괄호생략)
key, value = '삼성전자', 81000
print(key) # '삼성전자'
print(value) # 81000
```
위 방식이 언패킹이다.  
자바스크립트의 구조분해 할당 문법과 유사하다.  
세번째 할당에서 괄호가 생략되었는데, 파이썬에서는 자동으로 튜플로 인식된다.

for loop에서 in 키워드에 의해 key, value에 할당되는 원리이다.

</details>  
<hr>
<br>
