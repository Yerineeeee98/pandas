# numpy, pandas
- import numpy as np
- import pandas as pd

## ndarray 생성하기
- list = array (좀 더 고정된 느낌)
- ex) 2차원 배열
```python 
    arr2 = np.array( [[1.1, 2.2], [3.3 , 4.4]])
    print(arr2)
    print(type(arr2)) # [[1.1 2.2]
                      #  [3.3 4.4]]
                      # <class 'numpy.ndarray'> 
```        
- .ndim : 몇차원 배열인지 확인
- .shape : 바깥에 몇개인지, 안에 몇개인지

## np.arange 
- 정렬 
```python
    print(np.arange(10))
    # [0 1 2 3 4 5 6 7 8 9]
```

## ndarray 자료형
- 자료형 변경하는 법 
    - 1. float_arr1 = arr1.astype(np.float64) # .astype(내가 원하는 자료형)
    - 2. arr1 = np.array([1, 2, 3], dtype = np.float64) 선언할때 자료형 정의

## 산술연산
- 파이썬과 달리 print에서 바로 가능
```python
    print(arr * arr)
    print(arr + arr)
    print(1 / arr)
    print(arr ** 3)
```

## indexing과 slicing
- 파이썬과 달리 슬라이싱으로 값을 변경하면 원본도 바뀜
```python
    arr[2:5] = 10 # 2번쨰 부터 5번 미만 인덱스까지 값이 10으로 바뀜
```

## boolean값으로 선택
```python
    `names = np.array(['do', 'deft', 'hanhwa', 'yerin'])`
    여기서 yerin의 데이터만 추출하고 싶을 때
    `names == 'yerin'`
    # array([False, False, False, True])
```
```python
    'data = np.array(['exo', 'lol', 'baseball', 'min'])`
    여기서 yerin에 해당하는 데이터 값을 보고싶으면
    `data[names == 'yerin']` 
    # ['min']만 나오게 됨 
    # data[[False, False, False, True]] 여서 True값만 추출한것
```
- data[names == 'hong', 1] # 인덱스 접근
print(data[names == 'hong', :1]) # 슬라이싱 접근 노이해

## pd.Series()
- 인덱스와 결과값이 같이 나옴옴
- 음수 인덱스는 적용되지 않음
- 인덱스를 변경 할 수 있음
- `names = pd.Series(['kim', 'lee', 'park'], index=['a', 'b', 'c']) # 인덱스가 숫자가 아니여도 됨 ` 여기서 index=list('abc')도 가능
