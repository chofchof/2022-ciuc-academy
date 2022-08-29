# 자연어 처리 입문을 위한 강연과 실습



### 국가수리과학연구소 산업수학혁신센터

### 책임연구원 조진환



### 충남산학융합원 교육 프로그램 (2022년 9월 1일)



---



## 초록

AI를 활용한 자연어 처리 기술은 음성 인식 및 자동 번역은 물론 텍스트 분류 및 감성 분석을 넘어 질의 응답에 이르기까지 널리 사용되고 있다. 그림 또는 사진을 판별하는 AI 기술이 비교적 쉽게 접근할 수 있는데 비해  자연어 처리는 초보자들이 접근하기에 장벽이 높은 편이다.

이 강연에서는 자연어 처리를 위한 기본적인 이론과 도구를 다루는 방법에 대해 설명한다.



## 목차

1. 자연어 처리란?
2. 콘다(conda) 설치 및 가상환경 연습
3. 카운트 기반의 단어 표현과 벡터의 유사도



## 참고

- **딥 러닝을 이용한 자연어 처리 입문**, 유원준 및 안상준, https://wikidocs.net/book/2155



---



# 자연어 처리란?



### 위키백과 (한국어)

https://ko.wikipedia.org/wiki/자연어_처리

**자연어 처리**(自然語處理) 또는 **자연 언어 처리**(自然言語處理)는 <u>인간의 언어 현상</u>을 <u>컴퓨터와 같은 기계</u>를 이용해서 묘사할 수 있도록 연구하고 이를 구현하는 <u>인공지능</u>의 주요 분야 중 하나다. 자연 언어 처리는 연구 대상이 언어 이기 때문에 당연하게도 언어 자체를 연구하는 언어학과 언어 현상의 내적 기재를 탐구하는 언어 인지 과학과 연관이 깊다. 구현을 위해 수학적 통계적 도구를 많이 활용하며 특히 기계학습 도구를 많이 사용하는 대표적인 분야이다. <u>정보검색, QA 시스템, 문서 자동 분류, 신문기사 클러스터링, 대화형 Agent</u> 등 다양한 응용이 이루어지고 있다.



### 나무 위키

https://namu.wiki/w/자연 언어 처리

<u>컴퓨터</u>가 <u>인간의 언어</u>를 알아들을 수 있게 만드는 학문분야. <u>인공지능</u>의 하위 분야로, 일반적인 인공지능을 만들려던 1960년대의 시도가 실패한 후, 인간의 언어를 분석하고 해석하여 처리하는 인공지능이 세분화되면서 생긴 학문 분야. 흔히 우리가 아는 말하는 컴퓨터 및 인간과 대화하는 컴퓨터 관련 기술이 이 쪽에 속한다. 언어공학, 컴퓨터과학, 인공지능, 전산언어학의 연구 분야이며, 자연어를 컴퓨터로 해석하고, 의미를 분석하여 이해하고, 자동으로 생성하는 것 등에 관련된 분야다. 이 분야의 하위 분류로 <u>정보 추출, 자동 교정, 대화 시스템, 기계 번역</u> 등이 있다.



### Wikipedia (영어)

https://en.wikipedia.org/wiki/Natural_language_processing

#### Common NLP tasks

- **Text and speech processing** (텍스트 및 음성 처리)

  Optical character recognition (문자인식), Speech recognition (음성 인식), Speech segmentation (음성 분할), Text-to-speech (음성 변환), Word segmentation (단어 분할, 토큰화)

- **Morphological analysis** (형태소 분석)

  Lemmatization (표제어 추출), Morphological segmentation (형태소 분할), Part-of-speech tagging (품사 태깅), Stemming (어간 추출)

- **Syntactic analysis** (구문 분석)
- **Lexical semantics** (각 단어의 어휘 의미)
- **Relational semantics** (각 문장의 관계 의미)
- **Discourse** (담론, 각 문장 단위를 넘어선 의미)
- **Higher-level NLP applications**

![NLP](http://t1.kakaocdn.net/braincloud/homepage/article_image/c0265118-dbab-4ec9-93f1-3caac4efb039.png)

> 자연어처리(NLP) 분야의 핵심 과제로 자연어이해(NLU)와 자연어생성(NLG)을 꼽아볼 수 있습니다. NLU는 자연어 형태의 문장을 이해하는 기술을 가리킵니다. NLG는 자연어 문장을 생성하는 기술을 말하죠. 다시 말해 NLU와 NLG는 사람과 기계, 그리고 기계 간 사람이 자연어로 소통하는 데 필요한 기술이라고 보면 됩니다.
>
> 출처: https://m.blog.naver.com/koys007/221828611455, © 최요중 카카오브레인 연구원



---



# 콘다(conda) 설치 및 가상환경 연습



### A. Anaconda = `conda` + `python` + packages

#### Anaconda Distribution: https://www.anaconda.com/products/individual

![Anaconda Distribution](https://assets.anaconda.com/production/Products/Distro01.png?w=700&q=80&auto=format&fit=crop&crop=focalpoint&fp-x=0.5&fp-y=0.5&dm=1647546929&s=7a22f8ac8ef3c673d6522750d19073e5)

> 출처: https://www.anaconda.com/products/individual



### B. Miniconda3 or Miniforge3 or Mambaforge

#### (a) Miniconda3 = `python3` + `conda`

- https://docs.conda.io/en/latest/miniconda.html

- __Archive__: https://repo.anaconda.com/miniconda/
- **MS-Windows**: `Miniconda3-py39_4.12.0-Windows-x86_64.exe` (conda 4.12.0 + python 3.9)
- **설치 시 주의**: `Select Installation Type`에서 반드시 `Just Me (recommended)` 선택

#### (b) Miniforge3 = `python3` + `conda` + `--channel conda-forge` (추천)

- https://github.com/conda-forge/miniforge

- __Archive__: https://github.com/conda-forge/miniforge/releases
- **MS-Windows**: `Miniforge3-4.14.0-0-Windows-x86_64.exe` (conda 4.14.0 + python 3.9)
- **설치 시 주의**: `Select Installation Type`에서 반드시 `Just Me (recommended)` 선택

#### (c) Mambaforge = `python3` + `mamba` + `--channel conda-forge` (도전)

- https://github.com/conda-forge/miniforge

- __Archive__: https://github.com/conda-forge/miniforge/releases
- **MS-Windows**: `Mambaforge-4.14.0-0-Windows-x86_64.exe` (conda 4.14.0 + python 3.9)
- **설치 시 주의**: `Select Installation Type`에서 반드시 `Just Me (recommended)` 선택



### C. Getting started with conda (or mamba)

- https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html

- 먼저 `Miniforge Prompt` (또는 `Mambaforge Prompt`) 앱을 실행한다.

  

#### (a) conda 정보

```bash
conda --version
conda --help
conda info
```

#### (b) conda 가상환경 만들기

```bash
conda env list
conda create --name devel python=3.10
conda env list
```

#### (c) conda 가상환경 사용하기

```bash
conda activate devel
python --version
```

#### (d) conda 패키지 설치

```bash
conda list
conda install jupyterlab
jupyter lab
conda install numpy pandas matplotlib
conda list
```

#### (e) conda 가상환경 복사

```bash
conda env export > devel.yml
type devel.yml
```

#### (f) conda 가상환경 지우기

```bash
conda deactivate
conda env remove --name devel
conda env list
```


#### (g) conda 가상환경 붙이기

```bash
conda env create --file devel.yml
conda env list
conda list
```


#### (h) conda 패키지 지우기

```bash
conda remove numpy
conda list
```


#### (i) conda 패키지 업데이트

```bash
conda update --all
```



#### Conda Cheat sheet (PDF)

- https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html



### D. Linux utilities with conda (or mamba)

```bash
conda search grep
conda install m2-grep
conda list | grep numpy
```



### E. Jupyter Lab

```bash
jupyter lab
```

#### (a) `Launcher` > `Other` > `Text File`

- 한글이 들어있는 텍스트 파일(`test.txt`)을 만들어라.
- 이 텍스트 파일의 인코딩은? UTF-8 or CP949?

#### (b) `Launcher` > `Other` > `Terminal`

  ```bash
  type test.txt
  conda install m2-libiconv m2-libintl
  iconv -f UTF-8 -t CP949 test.txt > test_cp949.txt
  type test_cp949.txt
  ```

#### (c) `Launcher` > `Other` > `Markdown File`

- 마크다운 파일(`test.md`)을 만들어라.
- `Show Markdown Preview`를 찾아라!

#### (d) `Launcher` > `Notebook`과 `Launcher` > `Console`의 차이는?

#### (e) `Launcher` > `Other` > `Show Contextual Help`는 어떻게 사용하는가?




### F. 바로가기 아이콘 설정 (MS-Windows)

#### (a) Miniforge Prompt > 속성 > 바로가기

- 대상(T):
  ```bash
  %windir%\system32\cmd.exe "/K" %USERPROFILE%\miniforge3\Scripts\activate.bat devel
  ```
- 시작위치(S):
  ```bash
  %HOMEPATH%
  ```
- 설명(O):
  ```bash
  Miniforge3 Prompt (devel)
  ```
- 아이콘 변경(C)...
  ```bash
  %USERPROFILE%\miniforge3\Menu\console_shortcut.ico
  ```

#### (b) Jupyter Lab > 속성 > 바로가기


- 대상(T):
  ```bash
  %USERPROFILE%\miniforge3\python.exe %USERPROFILE%\miniforge3\cwp.py %USERPROFILE%\miniforge3\envs\devel %USERPROFILE%\miniforge3\envs\devel\python.exe %USERPROFILE%\miniforge3\envs\devel\Scripts\jupyter-lab-script.py "%USERPROFILE%/"
  ```
- 시작위치(S):
  ```bash
  %HOMEPATH%
  ```
- 설명(O):
  ```bash
  Jupyter Lab (devel)
  ```
- 아이콘 변경(C)...
  ```bash
  %USERPROFILE%\miniforge3\Menu\console_shortcut.ico
  ```



### G. GitHub

```bash
conda search git
conda install git
git clone https://github.com/chofchof/2022-ciuc-academy.git
cd 2022-ciuc-academy
git pull
```





