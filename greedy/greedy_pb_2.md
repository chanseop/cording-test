### 조건
- 1.첫줄에 N 자연수 갯수, M 더하는 횟수 ,K 최대 중복 횟수 의 자연수가 주어진다.
- 자연수 갯수대로 배열에 추가하고 추가하면서 숫자 비교해서 가장큰 숫자와 그다음으로 큰 숫자를 구한다.
- 예외일때 가장큰 숫자가 2번이상 배열에 들어갔을 때는 다른 인덱스이므로 중복해서 쓸수 있다

```python
n,m,k =map(int ,input().split())    #n,m,k 입력받기

# print(type(n))
# print(n,m,k)

array=list(map(int, input().split()))   #공백 배열 입력받기
# print(array[4])

max_index=-1
second_index=-1
sum=0
a=k

for i in range(len(array)):
    if max_index<=array[i]:
        second_index=max_index  #두번째 큰수 
        max_index=array[i]      #첫번째 큰수

        
for i in range(m):
    if(k!=0):   #반복횟수 조건
        sum=sum+max_index
        k=k-1       #반복횟수 횟수 차감
    else:
        sum=sum+second_index
        k=a
        

print(sum)
```
   
- 이 문제를 풀면서 고민했던 부분은 중복 횟수를 고민해줘야 된다는 것이였다.
그런데 숫자가 다 다른경우에는 중복 횟수만큼 가장 큰수를 더한 뒤 두번째 큰수를 한번 더하고 다시 가장 큰수를 더하면 된다는 생각을 쉽게 했지만
내가 어렵다고 생각한 부분이 입력값 n, m, k 가 5, 8 ,2 이고 배열이 [3 4 3 4 3]일 때 2번 인덱스랑 4번 인덱스랑 다른기 때문에 결과값이 4+4+4+4+4=28로 나온다.
그런데 결국 인덱스가 다르고 같은 숫자라도 가장 큰 수랑 두번째로 큰 수는 4로 동일하기 때문에 결과값에는 변화가 없다라는 것을 찾아 내었다.


### 느낀점

문제를 풀면서 두번째 인덱스와 네번째 인덱스를 어떻게 같은것을 확인할까 고민을 한 내가 너무 아쉽다.
좀더 프로그램적으로 생각하고 문제에 본질 결국 가장큰수와 두번째 큰수만 구하면 모든 경우를 해결할수 있다는
생각을 하지 못한게 아쉽다.



### 다른 풀이
```python
n,m,k=map(int, input().split())

data=list(map(int, input().split()))

data.sort()

first=data[n-1]
second=data[n-2]


count=int(m/(k+1))*k    # 가장 큰수가 더해지는 횟수 6회
count+=m%(k+1)          # 나머지가 있으면 무조건 가장큰수가 더해진다

result=0
result+= (count)*first      # 가장큰수 더해주기
result += (m-count)*second  # 두번째로 큰수 더해주기

print(result)
```
- 이 풀이는 예를 들어 m이 8 k가 3 일경우 가장큰수가 3번 반복후 두번째로 큰 수가 1번 반복하는 규칙을 수열로 풀어내서 4개의 index를 한 묶음으로 봐서 풀이를 한것이다.
