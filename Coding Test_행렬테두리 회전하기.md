```python
def solution(rows, columns, queries):
    answer = []
    array = [[0 for col in range(columns)] for row in range(rows)] # 0으로 초기화 된 배열 생성
    a = 1
    for row in range(rows):
        for col in range(columns):
            array[row][col] = a
            a += 1 # 행렬 1 씩 증가 생성
        
    for x1,x2,y1,y2 in queries:
        rotate = array[x1-1][y1-1]
        min_val = rotate
     
        for k in range(x1-1, x2-1): #왼쪽 세로 위로이동
            t = array[k+1][y1-1]
            array[k][y1-1] = t
            min_val = min(min_val,t)
    
        for k in range(y1-1, y2-1): # 아래쪽 가로 왼쪽으로 이동
            t = array[x2-1][k+1]
            array[x2-1][k] = t
            min_val = min(min_val,t)
        
        for k in range(x2-1,x1-1,-1): # 오른쪽 세로 아래로 이동
            t = array[k-1][y2-1]
            array[k][y2-1] = t
            min_val = min(min_val,t)

        for k in range(y2-1,y1-1,-1): # 상단 가로 우측으로 이동
            t = array[x1-1][k-1]
            array[x1-1][k] = t
            min_val = min(min_val,t)


        array[x1-1][y1] = rotate
        answer.append(min_val)

    return answer

```


```python

```
