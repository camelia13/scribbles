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
ffmpeg는 오디오, 비디오 파일을 변환할 수 있는 command line tool이다. Window, Mac, Linux에서 무료로 이용가능하다. 두 비디오 파일을 합치거나, 비디오에서 오디오만 추출할 때, 비디오에서 프레임을 추출할 때 등에 쓸 수 있다. 
파이썬에서도 subprocess와 결합하면 ffmpeg를 사용할 수 있다. video에 video 파일 이름, directory에 frame을 저장할 경로를 넣으면 된다. 더 자세한 내용은 https://ffmpeg.org/ 참조
```python
pip install ffmpeg 
ffmpeg_command = ['ffmpeg',
                 '-i', video,
                 '-vf', "scale=400:300", # input file
                 '{0}/%06d.jpg'.format(dirctory)]
subprocess.call(ffmpeg_command,
                stdout=subprocess.PIPE stderr=subprocess.PIPE)
```

* 몇 가지 error
  - cannot import name 'Optional' from 'torch.jit.annotations' ->   
  conda install pytorch==1.1.0 torchvision==0.3.0 cudatoolkit=9.0 -c pytorch  
  본인 cuda version에 맞는 pytorcr 설치. pytorch는 1.1.0 이상이면 무관한듯??  

  - E: Unable to locate package  
  try ```sudo apt update```
  
  - No such file or directory java: java  
  java jdk 설치 후 path 설정
  


