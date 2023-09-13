### 구현 알고리즘 

- 구현 : 머리속에 있는 알고리즘을 소스코드로 바꾸는 과정

    - 완전 탐색 : 모든 경우의 수를 주저 없이 다 계산하는 해결 방법 
    - 시뮬레이션 : 문제에서 제시한 알고리즘을 한 단계씩 차례대로 직접 수행

<br>

> **1. 상하좌우**

- n * n 크기의 정사각형 공간이 있다
- 가장 왼쪽 위 좌표는 (1,1), 가장 오른쪽 아래 좌표는 (n,n) 
- L(왼쪽), R(오른쪽), U(위), D(아래쪽)으로 한 칸 이동
- 최종적으로 여행자가 도착할 지점의 좌표 출력

>
    n = int(input()) # 공간의 크기 (5)
    plan = list(map(str,input().split())) # R R R U D D
    w = [1,1]
    
    for i in plan:
    
        if w[0] == 1 or w[1] == 1:
            if i in ['L','U']:
                continue
    
        if w[0] == n or w[1] == n:
            if i in ['R','D']:
                continue
    
        if i == 'R':
            w[1] += 1
        elif i == 'L':
            w[1] -= 1
        elif i == 'U':
            w[0] -= 1
        else:
            w[0] += 1
    
    print(w)

<br>
<br>

> **2. 시각**

- 정수 n이 입력되면 0시 0분 0초부터 n시 59분 59초까지 모든 시각 중 3이 하나라도 포함되는 모든 경우의 수를 구하시오.

>
    n = int(input()) # 5
    cnt = 0
    for i in range(n+1):
        for j in range(60):
            for k in range(60):
                if '3' in str(i)+str(j)+str(k):
                    cnt += 1
    
    print(cnt)

<br>
<br>

> **3. 왕실의 나이트**

- 8 x 8 좌표평면이 있을 때 나이트가 이동할 수 있는 경우의 수를 출력하는 프로그램을 작성하시오.  
- 이동 할 때는 L자 형태로만 이동할 수 있으며 정원 밖으로는 나갈 수 없음 

    - 수평으로 두 칸 이동한 뒤에 수직으로 한 칸 이동하기 
    - 수직으로 두 칸 이동한 뒤에 수평으로 한 칸 이동하기 

- ex) 나이트가 a1에 있을 때 이동할 수 있는 경우의 수는 2가지 ((3,2),(2,3))
* a일때 1, b일때 2, c일때 3...**

- 정수 n이 입력되면 0시 0분 0초부터 n시 59분 59초까지 모든 시각 중 3이 하나라도 포함되는 모든 경우의 수를 구하시오.

>
    location = input() # a1

    x = [2,2,-2,-2,1,1,-1,-1]
    y = [-1,1,-1,1,-2,2,-2,2]
    
    dic = {'a':1,'b':2,'c':3,'d':4,'e':5,'f':6,'g':7,'h':8}
    
    nowx = dic[location[0]]
    nowy = int(location[1])
    
    cnt = 0
    
    for i in range(8):
        row = nowx + x[i]
        column = nowy + y[i]
        # print(row,column)
    
        if 1<=row<=8 and 1<=column<=8:
            cnt += 1
    
    print(cnt)
    
<br>
<br>

> **4. 럭키 스트레이트**

- 현재 캐릭터의 점수를 n이라고 할 때 자릿수를 기준으로 반을 나누어 왼쪽의 각 자릿수의 합과<br>
  오른쪽의 각 자릿수의 합을 더한 값이 동일할 경우 'LUCKY'를 출력 
- 그렇지 않은 경우에는 'READY'를 출력함

>
    n = int(input())
    n = str(n)
    
    if sum([int(i) for i in n[:len(n)//2]]) == sum([int(i) for i in n[len(n)//2:]]):
        print('LUCKY')
    else:
        print('READY')

<br>
<br>

> **5. 문자열 재정렬**

- 알파벳 대문자와 숫자(0 ~ 9)로만 구성된 문자열이 입력으로 주어질 때 알파벳을 오름차순으로 정렬 후 모든 숫자들을 더한 값을 출력하시오

>
    import string

    s = input()
    alpha = string.ascii_uppercase
    result = sorted([i for i in s if i in alpha]) + [str(sum([int(i) for i in s if i not in alpha]))]
    
    print(''.join(result))

