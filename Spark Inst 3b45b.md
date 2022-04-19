# Spark Installation on Windows 10

참조 : 

[Spark Installation on Windows 10](https://dschloe.github.io/python/python_edu/00_settings/spark_installation_windows_10/)

**사전준비**

- 스파크를 설치하는 과정은 소개 하려고 한다.
- 사전에 파이썬 3만 설치가 되어 있으면 된다.
- 만약, 파이썬이 처음이라면 **[Anaconda](https://www.anaconda.com/products/individual)**를 설치한다.
- 자바 설치파일: **[Java SE 8 Archive Downloads (JDK 8u211 and later)](https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html)**
- 스파크 설치 URL: **[https://www.apache.org/dyn/closer.lua/spark/spark-3.2.0/spark-3.2.0-bin-hadoop3.2.tgz](https://www.apache.org/dyn/closer.lua/spark/spark-3.2.0/spark-3.2.0-bin-hadoop3.2.tgz)** (2022년 1월 기준)
- winrar 설치 파일: **[https://www.rarlab.com/download.htm](https://www.rarlab.com/download.htm)**
- winutils 설치파일: **[https://github.com/cdarlint/winutils](https://github.com/cdarlint/winutils)**
    - 주의 : 스파크 버전과 동일한 파일로 설치한다.

# 자바 설치

- 자바를 설치한다.
    - 폴더 경로를 C:\jdk 로 하였다

![Untitled](Spark%20Inst%203b45b/Untitled.png)

- 대상 폴더 경로를 C:\jre 로 하였다.

![Untitled](Spark%20Inst%203b45b/Untitled%201.png)

# winrar 설치

- .tgz 파일을 사용하기 위해 설치하였다.

# 스파크 설치

아래와 같이 설치를 한 후에 설치 폴더 이름을 spark로 변경한다.

![Untitled](Spark%20Inst%203b45b/Untitled%202.png)

- C드라이브에 위의 spark폴더를 복사해서 둔다.
- 폴더 안의 conf 폴더 안의 log4j.properties.template 의 파일을 메모장으로 연다.

![Untitled](Spark%20Inst%203b45b/Untitled%203.png)

- log4j.rootCategory=INFO, console 을 log4j.rootCategory=ERROR, console로 변경하였다.
    - 원래 문장을 다시 쓸 수 있기 때문에 주석처리 하였다.

![Untitled](Spark%20Inst%203b45b/Untitled%204.png)

- C드라이브에 winutils - bin 폴더를 생성한 후 winutils 파일을 넣어준다.

![Untitled](Spark%20Inst%203b45b/Untitled%205.png)

- C드라이브에 tmp\hive 폴더를 생성한다.
- CMD 관리자 권한으로 파일을 열어서 실행한다.

```bash
cd c:\winutils\bin
winutils.exe chmod 777 \tmp\hive

를 입력해준다.
```

# `c:\winutils\bin> winutils.exe chmod 777 \tmp\hive` 관리자 권한 약화

# 환경변수 설정

- 시스템 환경변수를 설정한다.
    - 각 사용자 계정에 `사용자 변수 - 새로 만들기 버튼`을 클릭한다.
- 변수 이름 - 변수 값으로 SPARK_HOME - C:\spark

![Untitled](Spark%20Inst%203b45b/Untitled%206.png)

- 변수 이름 - 변수 값으로 JAVA_HOME - C:\jdk

![Untitled](Spark%20Inst%203b45b/Untitled%207.png)

- 변수 이름 - 변수 값으로 HADOOP_HOME - C:\Windows

![Untitled](Spark%20Inst%203b45b/Untitled%208.png)

- PATH 변수를 편집한다. 아래 코드를 입력.
    - %SPARK_HOME%\bin
    - %JAVA_HOME%\bin

![Untitled](Spark%20Inst%203b45b/Untitled%209.png)

## 파이썬 환경설정

- 변수 이름 - 변수 값으로 PYSPARK_PYTHON - python

![Untitled](Spark%20Inst%203b45b/Untitled%2010.png)

- 변수 이름 - 변수 값으로 PYSPARK_DRIVER_PYTHON - jupyter
- 변수 이름 - PYSPARK_DRIVER_PYTHON_OPTS - notebook

![Untitled](Spark%20Inst%203b45b/Untitled%2011.png)

![Untitled](Spark%20Inst%203b45b/Untitled%2012.png)

- 위의 두 PYSPARK_DRIVER_PYTHON, PYSPARK_DRIVER_PYTHON_OPTS는 보류.

- CMD 파일을 열고 `c:\spark` 폴더로 경로를 설정 한다.
- pyspark를 실행한다.

![Untitled](Spark%20Inst%203b45b/Untitled%2013.png)

![Untitled](Spark%20Inst%203b45b/Untitled%2014.png)

- 

![Untitled](Spark%20Inst%203b45b/Untitled%2015.png)

> rd = sc.textFile("README.md")rd.count()
109
>