# scribbles
miscellaneous stuff

#### Python
* 2차원 배열 만들 때 아래처럼 만들면 안됨. M개 배열이 [0] * N 배열을 참조하기 때문임
```python
arg = [[0] * N] * M
arg[1][1] = 1 # arg[0][1], ... arg[M][1] 다 1됨 
```
그래서 아래처럼 해야함. 그냥 numpy 써도 됨
```python
arg = [[0] * N for _ in range(M)]
```

* list comprehensions. 간단한 함수는 lambda로 만들어 바로 aply 함수로 df에 적용시킬 수 있다. 다중 for문 축약할 수 있는데 더 헷갈리는 것 같다.
```python
dataframe.apply(lambda x: [i for i in x if condition])
```
