title: 맥에서 R(R Studio) Java 환경변수 설정하기
date: 2016-07-08 18:20:11
category:
- Dev
- R
tags:
- r
- r studio
- macOS
- java_home
- legacy java
thumbnailImage: RStudio-Ball.jpg
---
macOS에서 R Studio로 통계 패키지를 사용하려는데 두 가지 문제가 있었습니다.
- R 시스템 환경변수 설정
- 맥에서 java 버전

위의 두 가지였습니다.
R에서 'rJava'등의 java에 dependency가 있는 패키지를 사용하려면 R의 시스템 환경변수 'JAVA_HOME', 'Java libarary path' 두 가지를 정확하게 설정해줘야합니다.

<!-- more -->
터미널에서 `sudo R CMD javareconf`로 설정을 확인해보면 아래와 같이 맥에 설치된 java 정보와 시스템 변수로 저장된 경로가 표시됩니다.
![R javareconf](/assets/images/r_javaconf.jpg)

허나 실제로 R 및 R studio 를 실행해서 `Sys.getenv('JAVA_HOME')` 을 통해 확인을 해보면 아래와 같이 값이 설정되어있지 않습니다.
![R env javahome](/assets/images/r-javahome-env.png)

R을 실행해서 `Sys.setenv()`를 통해서 값을 설정해주어야 합니다. 하지만 위에서 확인한 경로대로  `/Library/Java/JavaVirtualMachines/jdk1.8.0_73.jdk/Contents/Home/jre`로 값을 변경해줘도 문제가 있습니다.
macOS에서 R과 java 버젼 호환문제인데요. 오라클에서 제공하는 최신버젼의 java는 R에서 사용할 수가 없습니다.

'애플 자바' 혹은 'legacy java'라고 불리우는 이전 버젼의 맥용 자바를 이 [링크](https://support.apple.com/kb/DL1572?locale=ko_KR&viewlocale=ko_KR)에서 받아 설치하셔야합니다.
이후 새로 설치된 자바의 경로를 아래와 같이 환경변수 값에 저장을 해주면 java를 이용한 패키지를 정상적으로 이용할 수 있습니다.
``` R
Sys.setenv(JAVA_HOME = '/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home')
```

![R javahome setting](/assets/images/r-javahome-setting.png)
