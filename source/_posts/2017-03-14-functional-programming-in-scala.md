---
title: 스칼라로 배우는 함수형 프로그래밍을 읽고서
date: 2017-03-14 20:40:47
category:
- Dev
- Functional Programming
tags:
- functional programming
- scala
- pure function
- side effect
---
'Functional Programming in SCALA'의 번역서인 '스칼라로 배우는 함수형 프로그래밍'을 공부하면서 복습을 위해 간단하게 리뷰 포스팅을 진행하려합니다.
- 제목 : 스칼라로 배우는 함수형 프로그래밍(Functional Programming in SCALA)
- 지은이 : Paul Chiudano, Runa Bjarnason
- 옮긴이 : 류광
- 출판사 : Jpub

<!-- more -->

## 제1부 함수형 프로그래밍 입문

### 제1장 함수형 프로그래밍이란 무엇인가?

간단한 예제들로 **부수효과(side effect)**의 단점과 side effect를 제거한 **순수함수(pure function)**에 대한 개념을 설명해주었다. side effect는 함수의 입력값에 따른 결과값(return 값) 이외의 행동들에 대한 것들이다. 예를 들어 변수의 값을 수정, 화면에 문자를 출력 등의 작업이 side effect에 해당한다.

순수하게 입력값에 따른 결과값만 반환하고 그 행동 이외에 어떠한 side effect가 없는 함수를 pure function이라 한다. 이러한 pure function은 해당 함수 스코프에서만 영향을 미치고 눈에 보이지 않는 부분을 수정하지 않으므로(책에서는 local reasoning이라고 언급) 버그를 낼 확률이 적으며, 디버깅시에 유용하다. 또한 외부와의 interaction이 없기 떄문에 모듈성이 증가해 재사용성도 증가한다.

**참조 투명성(referential transparency, RT)**에 대한 개념도 소개하고 있다. 예를들어, `val x = “bug bug debug”`라는 expression이 있고  코드의 다른 부분에서 x를 사용하는 부분이 있다고 가정했을 때, 그 x를 등호의 오른쪽 표현식인 “bug bug debug”라는 스트링으로 치환 했을때, 코드의 동작이나 의미에 아무런 영향이 없으면 ‘참조에 투명하다’ 라고 한다.

위에서 언급한 **참조 투명성**과 함수의 **순수성**의 개념이 비슷하면서도 다르게 느껴지는데 아직까지는 정확한 차이를 모르겠다.

책에서는 다음과 같이 설명하고 있다.
> 참조 투명성과 순수성
> 만일 모든 프로그램 p에 대해 표현식 e의 모든 출현(occurrence)을 e의 평가 결과로 치환해도  p의 의미에 아무 영향이 미치지 않는다면, 그 표현식 e는 참조에 투명하다(referentially transparent). 만일 표현식 f(x)가 참조에 투명한 모든 x에 대해 참조에 투명하면, 함수 f는 순수하다(pure).
> — 스칼라로 배우는 함수형 프로그래밍, p.12
