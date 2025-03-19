- python -m venv venv : 가상환경 생성
- siurce venv/Scripts/avtivate : 가상환경 활성화
- pip <module_name> : 모듈 설치
- pip freeze >> requirementes.txt : 현재 설치된 모듈 리스트 저장
- pip install -r requirements.txt : requirements.txt 기준으로 모듈 설치

## 00.numpy🧸
- 🐰 numpy불러오기 `import numpy as np`
- 🐰 np.arange 
    - 정렬 
        ```python
        print(np.arange(10))
        # [0 1 2 3 4 5 6 7 8 9]
        ```
- 🐰 np.array
     - 다차원 배열 생성
        ```python
            my_matrix = np.array([[1, 2, 3], [4, 5, 6]])
            # [[1 2 3]
             #   [4 5 6]]
         ```   
- 🐰 ndarray 자료형
     - `arr1 = np.array([1, 2, 3], dtype = np.float64)` 타입을 지정할 수 있음

    - `.astype(np.float64)` 형변환을 시키는 함수
    - `.dtype` 형을 확인하는 함수
    -  파이썬과 달리 직접 계산 가능
        - ```python
            data = 
            [[   1.     1.2    3. ]
            [-123.   123.     0. ]]
            print(data * 10)  #  [   10.    12.    30.]
            print(data + data ) # [   2.     2.4    6. ]
            ```
    - 비교도 가능
        - ```python
            print(arr > arr2)
            # [[False False  True]
             #   [ True  True  True]]
            print(arr == 3)
            # [[False False  True]
             #   [False False False]]
            ```
- 🐰 인덱싱과 슬라이싱
    - `arr = np.arange(10)`
        - `print(arr[7])` # 7
        - `print(arr[2:5])` # [2, 3, 4] # 파이썬과 달리 원본도 바뀜
    - 이차원 배열을 확인하려면 
        - `arr = np.array([[1, 2, 3], [4, 5, 6]])`
            - [[1 2 3]
                -  [4 5 6]]
            - `print(arr[0])` # [1, 2, 3]
            - `print(arr[1][1])` # [5]
            - `print(arr [1, 1])` # [5]
    - 삼차원 배열을 확인하려면
        - `arr3d = np.array([[[1, 2, 3], [4, 5, 6], [7, 8, 9]], 
            [[11, 12, 13], [14, 15, 16], [17, 18, 19]], 
            [[11, 22, 33], [44, 55, 66], [77, 88, 99]]])`
            - `print(arr3d[2][0][1])` # 22
            - `print(arr3d [2, 0, 1])` # 22
            - `print(arr3d[:1])` # [[[1 2 3] [4 5 6] [7 8 9]]]
            - `print(arr3d[:1, 1:, 2:])` # [6] [9]
        - 인덱스로 데이터 값 바꾸기
            - `arr3d[0, 1:, 2:] = 9999` # [6] -> [9999], [9] -> [9999]

- 🐰 불리언 값으로 선택
    -  `names = np.array(['hong', 'kim', 'hong', 'kim'])`
        - 'hong'의 데이터만 추출하고 싶을 때
            - `names == 'hong'` # array([ True, False,  True, False]) 
            - `data = np.array([['math', 60], ['math', 90], ['eng', 70], ['eng', 50]])`
                - `data[names == 'hong']` # ['math', '60'], ['eng', '70'] # data[[True, False, True, False]]에서 True만 출력한것
                - `data[names == 'hong', :1]` # ['math'], ['eng'] 

- 🐰 fancy indexing
    - `np.zeros((8, 4))` 
        - 
            [[0. 0. 0. 0.]
            [0. 0. 0. 0.]
            [0. 0. 0. 0.]
            [0. 0. 0. 0.]
            [0. 0. 0. 0.]
            [0. 0. 0. 0.]
            [0. 0. 0. 0.]
            [0. 0. 0. 0.]]
     - ```python
        for i in range(8):
        arr[i] = i # arr[1] = 1
        print(arr) 
        # [[0. 0. 0. 0.]
        #   [1. 1. 1. 1.]
        #   [2. 2. 2. 2.]
        #   [3. 3. 3. 3.]
        #   [4. 4. 4. 4.]
        #   [5. 5. 5. 5.]
        #   [6. 6. 6. 6.]
        #   [7. 7. 7. 7.]]
        ```
    - `arr[[4, 3, 0, 5]]` # [[]] 내가 원하는 특정 데이터에 접근
        - 
            array([[4., 4., 4., 4.],
                [3., 3., 3., 3.],
                [0., 0., 0., 0.],
                [5., 5., 5., 5.]])
        - `arr[[-3, -5, -1]]`
            -  
                array([[5., 5., 5., 5.],
                [3., 3., 3., 3.],
                 [7., 7., 7., 7.]])
    - `reshape()`
        - `arr = np.arange(32).reshape(8, 4)` 
            - 
                [[ 0  1  2  3]
                [ 4  5  6  7]
                [ 8  9 10 11]
                [12 13 14 15]
                [16 17 18 19]
                [20 21 22 23]
                [24 25 26 27]
                [28 29 30 31]]
            - `print(arr[[1, 5]])`
                - 
                    [[ 4  5  6  7]   # 배열의 1,5번째만 출력
                     [20 21 22 23]]

            - `print(arr[[1, 5], [2, 3]])`
                - 
                    [ 6 23]  # 배열의 1, 5번쨰 중에서 1번 배열의 2번째, 5번 배열의 3번쩨
            - `arr[[1, 5]][:, [2, 3]]` 
                - 
                    array([[ 6,  7],
                     [22, 23]]) # 배열의 1번째, 5번째 / 처음부터 끝까지에서 2,3번째 고르기
- 🐰 배열 전치
    - `arr.T` 축을 바꿀 때

- 🐰 numpy 함수
    - `np.random.standard_normal(size = (3, 3))` 
        - 3 * 3 배열을 임의로 만들 때
    - `np.sqrt()`
        - 배열에 루트를 씌울 때
    - ` np.abs()`
        - 절댓값을 씌울 때
    - `np.isnan()`
        - 현재 배열에 nan이 들어있는지 확인
---

## 01.datastructure🧸
- 🐰 Series
    - pandas에서 사용하는 1차원 배열
    - index를 사용할 수 있음
    - `arr = np.arange(100, 110)`
        - `s = pd.Series(arr)`
            - 
                0    100
                1    101
                2    102
                3    103
                4    104
                5    105
                6    106
                7    107
                8    108
                9    109 # 인덱스에 접근 하게 만듦

    - [-1] ❌ # 음수인덱스는 적용안됨
    - `names = pd.Series(['kim', 'lee', 'park'], index=['a', 'b', 'c'])` # index=list('abc')도 가능
        - 인덱스를 내가 직접 지정할 수 있음
        -  `names['a']` # 'kim'
        - ` names.values` # array(['kim', 'lee', 'park'], dtype=object)
        - `names.ndim` # 1 몇 차원인지
        - `names.shape` # (3, ) 1차원이여서 총 데이터 개수만 보여줌
- 🐰 fancy indexing
    - 
        `f = ['banana', 'apple', 'grape', np.nan]`
        ` s= pd.Series(f, index=list('abcd'))`
        s = a    banana
            b     apple
            c     grape
            d       NaN
        - s[['d']] # d       NaN
        - s.iloc[[3]] # d       NaN
        - s['a':'b'] # 글자로 된 index는 b도 포함되서 나옴옴
- 🐰 결측치(nan)처리
    - `isnull()` 
        - `nan`이 포함되면 True
    -   `s[s.isnull()]`
         - `s`배열에서 `nan`이 포함된 행만 출력
    - `s[s.notnull()]`
        - `s` 배열에서 `nan`이 포함되지 않은 행만 출력
    
- 🐰 DataFrame
    - 2차원 데이터 구조
    - 행, 열 구조
    - `pd.DataFrame()`
         - ![alt text](image.png) # 이런식으로 나옴
    - 
         ```python
          pd.DataFrame([
             [1, 2, 3],
             [4, 5, 6],
             [7, 8, 9]
            ], columns=['가', '나','다'])
        ```
      - ![alt text](image-1.png) # columns를 넣으면 위에 값이 바뀜

    - dict형태
        - 
            ```python
                     info = {
                     'name': ['kim', 'lee', 'park'],
                      'age': [10, 20 ,30],}
                     pd.DataFrame(info)
            ```
        
      ![alt text](image-3.png)
    - index 지정
        - `info_df.index = list('abc')`
    - 내가 필요한 column만 고르기
      - -`info_df[          ['age', 'name']       ]`

## 02.file_load_save🧸     
- 🐰 excel
    - excel 데이터 불러오기 
        - `pd.read_excel('data/DAMF2.xlsx')` ()안에 원하는 엑셀 주소 입력
- 🐰 csv
    - csv 데이터 불러오기
      - `pd.read_csv('data/DAMF2.csv')` ()안에 원하는 csv주소 입력

## 03.query🧸
- 🐰 seaborn
    - `import seaborn as sns`
    - `df = sns.load_dataset('titanic')` ()안에 원하는 데이터 이름

- 🐰 head(), tail()
    - `.head()` # 앞에서 다섯번째 데이터까지
    - `.tail()` # 뒤에서 다섯개의 데이터
    - `.head(10)` # ()안에 내가 보고싶은 데이터 개수를 적을 수 있음

-   🐰. info()
    - 데이터의 정보를 볼 수 있음

- 🐰 .value_counts()
      - ` df['who'].value_counts()` 앞에 원하는 값을 넣으면 특정값이 얼마나 자주 나오는지 알 수 있음
      - 

         who
         man      537
         woman    271
         child     83

- 🐰 정렬
    - `sort_index(ascending=False)`
        -  ascending = false로 해서 내림차순으로 정렬
    - `sort_values()`
        - `df.sort_values('age')` 
            - ()안에 내가 원하는 value값을 넣고 정렬하면 오름차순으로 정렬 됨
            - 이경우에는 나이가 어린순으로 정렬
        - ()안에 []로 value값을 여러개 적을 수 있음

- 🐰 indexing, slicing, 조건 필터링           