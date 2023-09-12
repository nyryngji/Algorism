### 정렬 알고리즘

- 정렬 : 데이터를 특정한 기준에 따라서 순서대로 나열

<br>

- **선택 정렬** : 가장 작은 데이터를 앞으로 보내는 과정을 n - 1번 반복 시 정렬 완료
>
    lst = [7,5,9,0,3,1,6,2,4,8] # 총 길이 10

    for i in range(len(lst)):
        min_index = i # 0
        for j in range(i+1, len(lst)): # 1부터 9까지
            if lst[min_index] > lst[j]: # 만약 lst[0]이 lst[1~9] 사이의 값보다 크면 
                min_index = j # 작은 값의 인덱스는 j
        lst[i], lst[min_index] = lst[min_index], lst[i]
    
    print(lst)

- 스와프 : 특정 리스트가 주어졌을 때 두 변수의 위치를 변경하는 작업

>
    arr = [3,5]
    arr[0],arr[1] = arr[1],arr[0]
    print(arr)

<br>

- **삽입 정렬** : 특정한 데이터를 적절한 위치에 '삽입'한다는 의미
>
    lst = [7,5,9,0,3,1,6,2,4,8]
    
    for i in range(1,len(lst)):
        for j in range(i,0,-1):
            if lst[j] < lst[j-1]:
                lst[j], lst[j-1] = lst[j-1], lst[j]
            else:
                break
    
    lst
    
<br>

- **퀵 정렬** : 기준을 설정 후 큰 수와 작은 수를 교환 후 리스트를 반으로 나눔
>
    arr = [5,7,9,0,3,1,6,2,4,8]

    pivot = arr[0]
    tail = arr[1:]
    
    left = sorted([i for i in tail if i <= pivot])
    right = sorted([i for i in tail if i > pivot])
    
    print(left + [pivot] + right)

<br>

- **계수 정렬** : 동일한 값을 가지는 데이터가 여러 번 등장하는 경우에 사용
>
    arr = [7,5,9,0,3,1,6,2,9,1,4,8,0,5,2] # 길이는 15
    
    count = [0]* (max(arr)+1) # 0이 10개
    
    for i in range(len(arr)): # 리스트에 있는 각 수가 몇 번 나오는지 계산
        count[arr[i]] += 1 
        
    print(count) # 0 2개, 1 2개..
    
    for i in range(len(count)): # 10번을 
        for j in range(count[i]): 
            print(i, end = ' ')

<br>

> **1. 위에서 아래로**

- 첫째 줄에 수열에 속해있는 수의 개수 N이 주어진다. 
- 둘째 줄부터 n개의 수가 입력된다. 
- 내림차순으로 정렬된 결과를 공백으로 구분하여 출력

>
    lst = sorted([int(input()) for i in range(int(input()))],reverse=True)
    print(' '.join(list(map(str,lst))))

<br>

> **2. 성적이 낮은 순서대로 학생 출력하기**

- n명의 학생 정보가 주어질 때 성적이 낮은 순서대로 학생의 이름 출력

>
    n = int(input())

    dic = []
    
    for i in range(n):
        a,b = map(str,input().split())
        dic.append((a,b))
        dic = sorted(dic, key=lambda x: x[1])
    
    print(' '.join([i[0] for i in dic]))

<br>

> **3. 두 배열의 원소 교체**

- 두 개의 배열 a,b가 있음 
- 두 배열은 n개의 원소로 구성되어 있으며 최대 k번 a배열 원소 하나와 b배열 원소 하나를 바꿀 수 있음 
- 이 때 a 배열의 합의 최댓값을 구하시오

>
    n,k = map(int,input().split())
    a = list(map(int,input().split()))
    b = list(map(int,input().split()))
    
    for i in range(k):
        a[a.index(min(a))], b[b.index(max(b))] = b[b.index(max(b))], a[a.index(min(a))]
    
    print(sum(a))
