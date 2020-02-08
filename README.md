# scribbles
miscellaneous stuff

#### Python
* Numpy 안쓰고 2차원 배열 만들기  
아래처럼 만들면 안됨. M개 배열이 [0] * N 배열을 참조하기 때문임
```python
arg = [[0] * N] * M
arg[1][1] = 1 # arg[0][1], ... arg[M][1] 다 1됨 
```
그래서 아래처럼 해야함
```python
arg = [[0] * N for _ in range(M)]
```

* list comprehensions  
간단한 함수는 lambda로 만들어 바로 aply 함수로 df에 적용시킬 수 있다. 다중 for문도 축약할 수 있는데 더 헷갈리는 것 같다.
```python
dataframe.apply(lambda x: [i for i in x if condition])
```

* subprocess  
os.system 대신 subprocess 모듈을 쓰라고 한다. 먼저 둘의 차이는 os.system은 shell command이고 subprocess.call(or subprocess.Popen)은 새로운 프로세서(child process)를 만들어 Poepn 객체와 데이터를 주고받을 수 있다. 그리고 shell에서 작업하는 것은 위험이 있어 피하라고 한다. 간혹 docker를 쓰다 보면 파이썬으로 실행되는 이미지가 있는데 그럴 때 subprocess로 ls 명령어를 쓸 수 있다. 그 외에도 기능이 많아 확인해보면 좋을 것 같다.


* ffmpeg
