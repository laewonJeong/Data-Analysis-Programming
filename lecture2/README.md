## ***1. Create a 4x4 numpy array of all True boolean's***
```python
#input
arr_size = (4, 4)

#Solution
bool_arr = 

#Print
print(bool_arr)

#Output
'''
[[ True  True  True  True]
 [ True  True  True  True]
 [ True  True  True  True]
 [ True  True  True  True]]
'''
```
- 4x4 numpy 배열에다가 True값을 넣어주면 됨
- numpy의 full을 이용
```python
np.full(arr_size,True)
```
---
## ***2. Extract all odd number from given arr.***
```python
# Input
arr = np.arange(30)

# Solution
arr = 

# Print
print(arr)

# Output
# [ 1 3 5 7 9 11 13 15 17 19 21 23 25 27 29]
```
- 주어진 arr에서 모든 홀수를 추출하면 됨
- ***Boolean Indexing***을 사용하여 홀수만 추출
```python
arr = arr[arr%2 != 0]
```
---
## ***3. Get the positions where elements of a and b match***
```python
# Input
a = np.array([1, 2, 3, 2, 3, 4, 3, 4, 5, 6])
b = np.array([7, 2, 10, 2, 7, 4, 9, 4, 9, 8])

# Solution
idx = 

# Print
print(idx)

# Output
# (array([1, 3, 5, 7]),)
```
- a와 b의 요소가 일치하는 위치를 구하면 됨
- 위치가 0 ~ 10 이고 a, b 1번째 위치의 요소가 둘 다 2로 같고, 3번째 위치에 요소도 2로 같고, 5번째 위치에 요소도 4로 같고, 7번째 위치에 요소도 4로 같음
- 따라서 답은 [1, 3, 5, 7]
- numpy의 where을 사용하여 추출함
```python
idx = np.where(a==b)
```
---
## ***4. Find the mean, median, standard deviation of iris's sepallength (1st column)***
```python
# Input
url = 'https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data'
iris = np.genfromtxt(url, delimiter=',', dtype='object')
sepallength = np.genfromtxt(url, delimiter=',', dtype='float', usecols=[0])

# Solution
mu, med, std = 

# Print
print(mu, med, std)

# Output
# 5.843333333333334 5.8 0.8253012917851409
```
- iris's sepallength에서 mean, median, standard값을 구하면 됨
- 각각 numpy의 mean(), median(), std()를 사용
```python
mu, med, std = np.mean(sepallength), np.median(sepallength), np.std(sepallength)
```
---
## ***5. Find the duplicate entries (2nd occurrence onwards) in the given numpy array and mark them as True. First time occurrences should be False.***
```python
# Input
np.random.seed(100)
a = np.random.randint(0, 5, 10)
print('Array: ', a)

# Solution
## Create an all True array
out = 

## Find the index positions of unique elements
b,unique_positions = 

## Mark those positions as False
out[unique_positions] = False

print('Duplicate entrie: ', out)

# Output
# Array:  [0 0 3 0 2 4 2 2 2 2]
# Duplicate entrie:  [False  True False  True False False  True  True  True  True]
```
- 지정된 숫자 배열에서 중복 항목(두 번째 발생 이후)을 찾아 True로 표시하고 처음 발생하는 항목은 False로 표시
- We use **full()** for create an all True array
```python
out = np.full(10,True)
```
- We use **unique()** for find the index positions of unique elements. **(return_index = True)**
```python
np.unique(a, return_index = True)
```
---
## ***6. Combine ser1 and ser2 to form a dataframe.***
```python
# Input
ser1 = pd.Series(list('abcedfghijklmnopqrstuvwxyz'))
ser2 = pd.Series(np.arange(26))

# Solution
df = pd.DataFrame(

# Print
print(df.head())

# Output

#  col1  col2
#0    a     0
#1    b     1
#2    c     2
#3    e     3
#4    d     4
```
- ser1과 ser2를 결합하여 데이터프레임을 구성을 하면 됨
- ser1과 ser2를 결합하는데 pandas의 concat()을 사용함
```python
df = pd.DataFrame(pd.concat([ser1,ser2],axis=1,keys=['col1','col2']))
```
---
## ***7. Check if df has any missing values.***
```python
# Input
df = pd.read_csv('https://raw.githubusercontent.com/selva86/datasets/master/Cars93_miss.csv')
print(df.head())

# Solution
print('\nIs there any missing value?:', )

# Output
'''
  Manufacturer    Model     Type  ...  Weight   Origin           Make
0        Acura  Integra    Small  ...  2705.0  non-USA  Acura Integra
1          NaN   Legend  Midsize  ...  3560.0  non-USA   Acura Legend
2         Audi       90  Compact  ...  3375.0  non-USA        Audi 90
3         Audi      100  Midsize  ...  3405.0  non-USA       Audi 100
4          BMW     535i  Midsize  ...  3640.0  non-USA       BMW 535i

[5 rows x 27 columns]

Is there any missing value?: True
'''
```
- df에 missing value가 있으면 True를 출력하고 없으면 False를 출력하면 됨
- isnull().values.any()를 사용하면 missing value가 하나라도 있으면 True를 반환하고 없으면 False를 반환해줌
```python
print('\nIs there any missing value?:', df.isnull().values.any())
```
---
## ***8. Create a TimeSeries starting 2021-01-01 and 10 weekends (sundays) after that having random numbers as values?***
```python
# Solution
ser = pd.Series(
print(ser)

# Output
'''
0   2021-01-03
1   2021-01-10
2   2021-01-17
3   2021-01-24
4   2021-01-31
5   2021-02-07
6   2021-02-14
7   2021-02-21
8   2021-02-28
9   2021-03-07
dtype: datetime64[ns]
'''
```
- pd.date_range()를 사용
- pd.date_range()안에 시작일을 '01-01-2021'로 설정하고, 10 weekends이기 때문에 period는 10으로 설정하고, freq를 'W'로 설정해줌
- freq = 'W'의 의미는 빈도가 한 주가 끝날때 마다 임
```python
ser = pd.Series(pd.date_range('01-01-2021',periods=10,freq='W'))
```
---
## ***9. In df, compute the mean price of every fruit using grouping function.***
```python
# Input
df = pd.DataFrame({'fruit': ['apple', 'banana', 'orange'] * 3,
                   'rating': np.random.rand(9),
                   'price': np.random.randint(0, 15, 9)})

# Solution
df.groupby(

# Output
'''
fruit
apple     9.666667
banana    6.333333
orange    6.666667
Name: price, dtype: float64
'''
```
- grouby()를 사용하여 각 fruit의 mean price를 구하면됨
```python
df.groupby('fruit')['price'].mean()
```
---
## ***10. Join two dataframes df1 and df2 for intersection items on use_id.***
### ***For df2, please select only use_id, platform, device columns not all columns for merging.***
```python
# Input
base_path = 'https://raw.githubusercontent.com/shanealynn/Pandas-Merge-Tutorial/master/'
df1 = pd.read_csv(base_path + 'user_usage.csv')
df2 = pd.read_csv(base_path + 'user_device.csv')

# Solution
pd.merge(
```
- use_id의 교차점 항목에 대해 데이터 프레임 df1과 df2 두 개를 결합하면 됨
- 하지만, df2에서는 use_id, platform, device 열만 선택하여 결합해야 됨
- 그래서 데이터프레임을 하나 더 만들었음 -> df2에서 use_id, platform, device 열만 선택한 데이터프레임
```python
pd.merge(df1,pd.DataFrame(df2,columns=['use_id','platform','device']), on='use_id')
```














