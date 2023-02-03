### 입력조건
- 첫째 줄에 숫자 카드들이 놓인 행의 개수 N과 열의 개수 M의 공백을 기준으로 하여 가각 자연수로 주어진다.
- 둘쨰 줄부터 N개의 줄에 걸쳐 각 카드에 적힌 숫자가 주어진다. 각 숫자는 1 이상 10000 이하의 자연수 이다.

### 출력 조건
- 첫째 줄에 게임의 룰에 맞게 선택한 카드에 적힌 숫자를 출력한다.
```python
n,m=map(int,input().split())

matrix=[]   #빈 배열 만들기

for i in range (n):
    array=list(map(int, input().split()))   #공백 숫자 배열로 받기
    array.sort()                            #배열 정렬
    matrix.append(array)                    #matrix배열안에 배열로 넣기

min_index=matrix[0][0]

for i in range(n):
    if min_index<matrix[i][0]:              #0번 index끼리 비교후 가장 큰 숫자 찾아내기
        min_index=matrix[i][0]
        
# print(matrix)
print(min_index)
```
### 느낀점
- 이문제는 처음에 순서대로 배열에 넣어서 행렬 형태로 넣어서 풀었는데 하나하나 비교해야 되기 때문에 2중 for문을 한번 더 써야되는 상황이였다. 그런데 처음에 넣을때부터 정렬을 한다음 넣으면 열에 0번째 index끼리만 비교하면 되겠다 생각이 들어서 그렇게 풀었다.


### 다른풀이
```python
n,m=map(int, input().split())

result=0

for i in range(n):
    data=list(map(int, input().split()))
    min_value= min(data)
    print('!!!!',min_value)
    result=max(result, min_value)
    print('@@@@',result)

print(result)
```
- 위에 풀이는 입력을 받고 바로 가장 작은 값을 출력후 min_value안에 넣어주고 그 작은 값들을 result안에 넣은뒤 나중에 최종적으로 result에서 가장 큰 값을 찾아내는 방법이다.
