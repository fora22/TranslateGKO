# PYTHON: PYTHONICNESS

프로그래밍에 있어 파이썬이 무엇을 할 수 있고 어떻게 사용되는지 이해하는 데 있어, 파이썬 개발자에게 추천되는 프로그래밍에 적용 가능한 독특한 스타일이 있다.



## 파이썬의 선

파이썬 내에서 제공되는 파이썬 프로그래밍에 권장되는 원칙이다. 이는 아래를 코드로 확인할 수 있다.

```python
import this
```



## PEP8

파이썬 개발자로부터 제안된 여덟 가지의 스크립팅 방식은 PEP8이라 불린다.

모듈은 짧고, 소문자로 된 이름을 가져야만 한다.

클래스 명은 대문자로 지어져야 한다.

대부분의 변수와 함수는 언더바(_)와 소문자로 작성되어야 한다.

상수(값이 절대 변하지 않는 변수)는 언더바(_)와 함께 대문자로 작성되도록 한다.

파이썬의 키워드(class, if와 같은)와 충돌 가능성이 있는 이름은 끝에 언더바(_)를 추가해주어야만 한다.

한 줄의 문자형은 80 자 이내로 작성하도록 한다.

`from module import *` 는 되도록 사용하지 않는다. 



## 진입점(Entry Point)

C/C++과 같은 언어는 `main()`과 같이 프로그램이 시작되는 함수인 진입점이 있는 반면, 파이썬은 그러한 것이 없다. 그 대신, 파이썬은 현재 작업 중인 스크립트가 실행되는지 알려주는 특별한 변수인 `__name__`을 사용한다. 만일 해당 스크립트가 주 실행파일일 때, 변수 `__name__`에는 `"__main__"` 값으로 설정된다.

```python
if __name__ == "__main__":
    statements
```

위 조건 하에 작성된 코드와 구문들은 다른 스크립트에서 모듈로 불러올 경우 실행되지 않는다. 여기서 `==` 연산자는 `is` 논리 연산자로 대체될 수 없다.



# 파이썬: 파일 관리

과학적 연구 혹은 인공지능과 같은 목적의 파이썬 스크립팅에서, 계산되어야 할 입력 데이터는 파이썬의 콘솔창으로 입력하는 방법은 비효율적이다. 이러한 경우, 입력 데이터를 파일로 읽는 방법을 사용할 수 있다.



## 파일 열기

파이썬을 통해 파일을 읽거나 편집하기 전에, 그 파일은 직접 열어야 한다. open() 함수는 사용자가 파일을 열고 싶어할 때 여는데 사용된다. 



```python
open("filename.txt")
```

| 옵션 | 설명                           |
| ---- | ------------------------------ |
| `r`  | 읽기 모드(기본)                |
| `w`  | 작성 모드(고쳐쓰기)            |
| `a`  | 추가 모드(새 코드 추가)        |
| `rb` | 이진 읽기 모드(text 파일 제외) |
| `wb` | 이진 작성 모드(text 파일 제외) |



`close()` 메소드는 현재 열려 있는 파일들을 닫기 위해 사용한다. 파일을 닫는 것은 리소스 낭비를 방지하기 위해 매우 중요하다. `try`/`except` 혹은 `with` 문을 사용하여 예외의 경우에도 파일을 항상 닫을 수 있도록 한다.



```python
variable = open("file.txt", "r")
variable.close()
```



### `with` 문

with 구문은 들여쓰기 된 코드 블록 안에서만 사용 가능한 임시 변수를 만들어낸다. 이 문구를 사용하여 파일을 열 때, 예외가 발생할지라도 결국 파일을 자동적으로 닫히게 한다.

```
with open("file.txt") as variable:
    statements
```



### 절대경로 & 상대경로

다른 프로그래밍 언어와 같이, 파이썬은 절대경로와 상대경로를 가지고 있다. 단일 백슬래쉬가 문자열 내에서 기능을 실행하는 탈출문자이기 때문에, 경로를 지정할 때 두 개의 백슬래쉬 `\\`를 쓴다.



> variable = open("path\\file.txt")



## 파일 읽기

텍스트 기반의 파일을 열고 난 후, 파이썬은 read() 메소드를 사용하여 파일의 내용을 읽을 수 있다.그 메소드의 인수는 그 방법이 읽을 바이트의 크기를 나타낸다.

Read 메소드는 같은 파일에 계속해서 사용 될 수 있지만, 그것은 파이썬이 마지막으로 읽은 지점에서 계속될 것이다. 인수가 없다면, read 방법은 그것이 마지막으로 중단한 곳에서 텍스트의 나머지를 읽는다.

```python
with open("path\\file.txt"):
    print(variable.read(16))	# 내용의 시작점부터 16바이트를 읽음.
    print(variable.read(4))		# 이전의 16바이트를 읽은 시점에서 4바이트를 읽음.
    print(variable.read())		# 이전에 읽은 4바이트 지점부터 나머지를 읽음.
    print(variable.read())		# 더 이상 읽을 내용이 없으면 텍스트를 읽지 않음.
```
`Readlines()` 메서드는 텍스트의 각 줄을 반환하는데 사용한다. 메서드는 인수를 받지만, `read()` 메소드와 같이 읽을 바이트 수를 의미한다.



오롯이 문자열의 첫번째 줄만 읽는 `Readline()` 메서드와 혼동하지 않도록 한다.

```python
<file.txt>

첫번째 줄

두번째 줄

...

...

마지막 줄
```

```python
with open("path\\file.txt") as variable:
    print(variable.readlines())
    print(variable.readline())
```

```python
['첫번째 줄.\n','두번째 줄.\n','마지막 줄']
첫번째 줄
```



## 루프를 사용하는 출력문

텍스트 기반 내용의 각 줄은 `for` 루프문을 사용하여 읽을 수 있다.

```python
for variable in file:
    print(variable)
```



## 파일 쓰기

파이썬에서,  파일은 텍스트 기반 파일 객체의 write() method에 의해 만들어지거나 작성(덮어쓰기)될 수 있다.  작성을 할 때, 사용자는 덮어쓰기와 덧붙이기의 두 가지 옵션 중 골라 사용할 수 있다.

```python
<file.txt>
First line here.
Second line there.
Last line somewhere.
```

Overwrite mode(덮어쓰기)는 이전에 존재하는 모든 내용을 지워버리고 처음부터 새롭게 작성을 한다.



```python
with open("path\\file.txt", "w") as variable:
    variable.write("TEXT OVERWRITTEN!")
<file.txt>
TEXT OVERWRITTEN!
```

반면에,  Append mode(덧붙이기)는 이전의 내용들을 지우지 않고 내용의 마지막에서부터 작성을 계속할 수 있다.

```python
with open("path\\file.txt", "a") as variable:
    variable = variable.write("TEXT APPENDED.")
	print(variable)
<file.txt>
First line here.
Second line there.
Last line somewhere.TEXT APPENDED.
```

성공적으로 작성이 되면, write() 메서드는 작성된 바이트의 수를 반환한다.



## 파일 만들기

새로운 파일은 기존의 파일에 작성하는 것만으로 묶이지 않는 write() 메서드를 사용함으로써 만들어질 수 있다.

```python
with open("path\\new-file.txt", "w") as variable:
    variable.write("NEW FILE CREATED!")
<new-file.txt>
NEW FILE CREATED!
PYTHON: PACKAGE
```

파이썬은 쉽게 다운로드받고 주문형으로 사용될수 있는 다양한 패키지를 가지고 있다. 이번 챕터는 그 패키지가 무엇인지와 그 패키지를 어떻게 스크립트에서 구현하는지에 대해 설명한다.



## 모듈

파이썬 모듈은 쉽게 말해 py. 확장자를 가진 파이썬의 소스코드이다. 개발자는 클래스나 함수를 포함하는 그들만의 코드를 개발할 수 있으며, 배포된 Python 파일에서 해당 코드를 호출하는 작업을  import 키워드를 통해 호출할 수 있다.



#### import 모듈

```python
module.function()
```

위의 접근법은 해당 기능을 사용할 때마다 모듈의 이름이 호출되는 것을 아직도 필요로 한다. 여전히 모듈의 기능을 사용하는 동안에 모듈의 호출을 무시하기 위해서는, 사전에 from 키워드를 사용해야 한다.



```python
from module import function1, function2
from module import function as name
```

그러나, 모듈이 해당 기능의 사용을 위해 호출이 되지 않았기 때문에, 기능의 호출로 인해 발생되는 잠재적인 충돌이 있다. 기능이 보장된 독특성으로 지명되지 않는 한, 모듈을 불러오기 위해 이전의 접근을 사용하는 것이 안전하다.



#### Package

Package는 Python 모듈 혹은 하위 모듈의 집합을 포함하는 폴더의 디렉토리이다. 모든 패키지 폴더는 공란, 혹은 보편적인 이름으로 발생되는 디렉토리간의 에러를 방지하는 현재 패키지의 디렉토리 경로를 포함하는 init.py라고 불리는 특별한 파이썬 파일을 가지고 있어야만 한다.

```python
import package.module
from package.module import function
Python Package Index
```

Python 패키지 인덱스(PyPI)는 외부 모듈이 저장된 사이트이다(https://pypi.python.org/pypi). 모듈과 패키지를 다운로드하고 설치하기 위해서는, pip이라 불리는 소프트웨어가 필요하다.



#### PIP

pip 소프트웨어는 파이썬 패키지를 설치하고 관리하기 위해 필요한 패키지 관리 시스템이다. 최근 들어, pip은 현재 Python의 유포와 함께 기본적으로 설치된다. 사용자는 온라인으로 pip만 설치할 수도 있다. 패키지의 설치와 관리는 명령 프롬프트를 사용한다.

> Name Description Command(이름 설명 명령어)

```python
Installation	패키지 설치	pip install package
Remove			패키지 삭제	pip uninstall package
List			패키지 리스트 출력	pip list
```

Windows에서 Python을 사용할 때, pip만 사용하는 것 대신에 python -m pip을 사용하는 것을 추천한다.



#### python -m pip

이 명령어는 환경변수에서 Python으로 지정된 Python 번역기 아래의 pip에 접근하는 것을 의미한다. 이것은 가상 환경을 이용할 때에도 각 번역기에 의한 패키지 관리가 더욱 쉽게 조작할 수 있게 한다. 다른 버전의 Python이 설치되어 있을 때, 32비트의 Python 3.5라고 부른다.

```
py -3.5-32 -m pip
PYTHON: VIRTUAL ENVIRONMENT
```

C언어 기반의 프로젝트는 스크립트를 수행할 때, 헤더 파일들과 라이브러리들을 개별적으로 포함시키는 것을 필요로 한다. 반면, Python은 번역기 디렉토리의 하위에 모듈의 설치만을 필요로 한다.



그러나, 여러 개의 Python 프로젝트를 작업할 때, 단일 통역기에 모든 패키지들을 설치하는 것은 편리하지도 않을 뿐더러 비효율적이다. 가상 환경을 사용하는 Python 환경을 분리하는 것이 필수적인 이유이다.



#### venv Package

Python3에는 기본적으로 포함된 가상환경 패키지인 venv가 있다. 이 패키지는 선택적으로 시스템 사이트의 디렉토리에서 고립된 그들만의 사이트 디렉토리와 함께 가벼운 가상환경을 만드는 것에 도움을 준다.

각 가상환경은 그들만의 고유한 Python 바이너리를 가지고 있으며, 사이트 디렉토리에 설치된 파이썬 패키지의 집합을 가질 수 있다.



#### 환경 만들기

원하는 프로젝트 디렉토리에 .venv라는 이름의 가상환경을 만드는 것은 다음과 같다.

> python -m venv D:\Workspace\Python\project.venv

환경 활성화

여기서 "활성화"라는 용어는 명령 프롬프트 혹은 터미널에서 가상환경을 작동시키는 것을 의미한다.  이것이 가상 환경에서 스크립트를 실행할 때에는 불필요한 반면에, 콘솔에서 pip을 사용하여 패키지를 설치할 때에는 활성화가 요구된다.



윈도우:

```
D:\Workspace\Python\project.venv\scripts\activate.bat

Unix (e.g. Linux and macOS):

source-\Workspace\Python\project\.venv\bin\activate
```



##### 비활동적인 환경

활성화된 콘솔의 가상환경에서 벗어나기 위해서, 사용자는 가상환경을 "비활성화" 할 필요가 있다.



##### 비활성화

이것은 명령어 PATH=D:\Workspace\Python.venv\Scripts\deactivate.bat에 들어가는 것과 같다. 이 때문에, 가상환경 디렉토리를 재배치하는 것은 경로 인식을 불가능하게 하는 비활성화 명령을 유발한다.



# Python: NUMPY

Numpy는 파이썬에서 사용되는, 다중 행렬을 보조하는 지극히 위력있고 유용한 라이브러리이다. 가장 잘 알려진 과학적 라이브러리들 중 하나로써, 그것은 Matplotlib, TensorFlow 및 cetera와 같이 다른 잘 알려진 라이브러리에서 실행된다.

NumPy 라이브러리를 설치하기 위해, 윈도우의 명령 프롬프트를 열고 아래의 명령어를 실행한다.

> python -m pip install numpy

NumPy가 거대한 과학적 라이브러리일 뿐 아니라 아직 성장하고 있기 때문에, 이 챕터는  배열의 기초적 사용법을 간단하게 소개하려 한다. API에 더 많은 정보를 원한다면, URL: https://numpy.org/ 에 접속해라.



## NumPy 배열

NumPy 배열은 굉장히 유연한 행렬이다. 파이썬 리스트의 수많은 객체에 비교해보면, 배열은 속도에서의 이점과 메모리 관리에서의 효율성 두 부분 모두에서 더 나은 수행능력을 가지고 있다.



## NUMPY DECLARATION : NumPy 선언

```python
variable = np.ndarray(shape = (2, 3))
print(variable)
[[800191312     32765 800196048]
 [    32765 870097920     32765]]

```

이것은 주어진 크기에 기반하여 NumPy 배열 객체를 만들지만, 그것의 값은 임의로 정해진다.

NumPy 배열의 초기화는 다음과 같이 이루어진다.

> import numpy as np
>
> 

## NUMPY INITIALIZATION : NumPy 초기화
```python
variable = np.array([[1, 2, 3], [4, 5, 6]])
print(variable)
[[1 2 3]
 [4 5 6]]
```

이는 주어진 크기에 기반하여 NumPy 배열 객체를 만들지만, 크기가 큰 배열이나 고차원의 배열을 만드는 데에 있어서는 불이익을 가진다.



더욱 편리하게 배열을 생성하기 위해 사용되는 더 많은 NumPy 메서드가 존재한다.



| Numpy    | 배열         | 설명                                                         |
| -------- | ------------ | ------------------------------------------------------------ |
| np.zeros | shape        | 배열의 크기에 기반하여 0으로 채워져 있는 NumPy를 만든다.     |
| np.ones  | shape        | 배열의 크기에 기반하여 1로 채워져 있는 NumPy를 만든다.       |
| np.eye   | N            | N * N 크기의 NumPy 단위행렬을 만든다.                        |
| np.full  | shape, value | 배열의 크기에 기반하여 넣은 값으로 채워져 있는 NumPy를 만든다. |



## NumPy 요소

NumPy 배열의 요소에 접근하는 것은 Python의 반복 가능한 객체와 비슷하지만, 그것의 구문은 다르다.

```python
import numpy as np
variable = np.array([[1, 2, 3], [4, 5, 6]])

print(variable[0])		# >> OUTPUT: [1, 2, 3]
print(variable[0, 1])	# >> OUTPUT: 2
```



### NumPy shape

NumPy의 형태는 len()과 같은 Python의 반복가능 객체에서 사용하는 메서드로부터 추출될 수 없다.

import numpy as np
variable = np.array([[1, 2, 3], [4, 5, 6]])

variable.shape		# >> OUTPUT: (2, 3)
variable.shape[0]	# >> OUTPUT: 2

### NumPy indexing

"인덱싱"이라는 용어는 특정 범위만으로 배열을 나누는 것을 의미한다. 각각의 크기는 콜론(:)을 사용하여 색인이 되어있고, 쉼표(,)를 통해 구분된다. 색인하는 것은 수많은 객체의 부분처럼 같은 규칙을 공유한다.

```
n:m : start indexing from n^th^ element (included) to m^th^ element (excluded)

: :색인을 처음부터 끝까지 시작하고, 따라서 색인을 건너뛴다.
```

```
import numpy as np
variable = np.array([[1, 2, 3], [4, 5, 6]])

print(variable[:, 1:-1])
[[1 2]
 [4 5]]
```



## Python : MATPLOTLIB

Matplotlib은 다양한 hardcopy 형식과 플랫폼 전반에 걸친 상호작용 환경에서 작품의 품질 수치를 산출하는 Python 2D 구성 라이브러리이다. 개발자는 단 몇 줄의 코드만으로 구성, 히스토그램, 동력 스펙트럼, 막대 차트, 에러 차트, 산점도 등을 만들어 낼 수 있다.

Matplotlib 라이브러리를 설치하기 위해서, 윈도우의 명령 프롬프트를 열고 아래의 명령어를 입력한다.

```
python -m pip install matplotlib
```

Matplotlib이 거대한 과학적 라이브러리이고 아직 성장중이기 때문에, 이 챕터에선 기초적인 용어와 그것의 매커니즘을 간단하게 설명할 것이다. 더 많은 정보를 원한다면, 다음의 URL로 들어갈 것.

URL : https://matplotlib.org/



### 용어

Matplotlib은 익숙치 않은, 다양한 용어 사용자와 개발자가 있다. 이 부분은 이쯤에서 이해에 도움을 줄 수도 있는 라이브러리에서 사용되는 용어를 제공한다.  아래는 공식 Matplotlib 사이트의 내용이다.

```
<img src=".\.images\Python\matplotlib_terminology.png" width=100%
Figure #. Matplotlib terminology.
Figure
Figure is considered an empty window of easel (a standing frame for a canvas):

<img src=".\.images\Python\matplotlib_figure_no_axes.png" width=70%>
```

그림 #. 축이 없는 Matplotlib 그림

matplotlib.pyplot.figure()과 같은 API를 사용하는 그림을 누르면 아무것도 없는 순백의 윈도우 배경이 반환된다.

Axes

Axes(subplot)는 easel 위로 올라가는 캔버스로 고려되는 데이터 공간이 있는 이미지의 영역이다.

Axes와 완전히 다른 axis(축)과 혼동하지 말자. 다음은 네개의 빈 axes가 있는 형태이다.

```
<img src=".\.images\Python\matplotlib_figure_with_axes.png" width=70%>
```

그림 #. 네개의 axes가 있는 Matplotlib 형태

Matplotlib.pyplot.subplot() 혹은 matplotlib.pyplot.subplots()과 같은 API는 그림과 단일 혹은 다중의 빈 axes를 동시다발적으로 반환한다.

