<style>body {font-family: D2Coding;}</style>

# 함수

> 시스템을 나누는 기준의 변화  
> 초창기 -> 루틴:하위루틴  
> 포트란<sup>[1](#1)</sup> & PL/1<sup>[2](#2)</sup> -> 프로그램:하위프로그램:함수  
> 오늘날 -> `함수`

- 어떤 프로그램이든 가장 기본적인 단위는 `함수`이다  
- 3장에서는 `함수를 잘만드는 법을` 소개한다  

![코드예3-1]()  
길고, 중복, 이상한 문자열, 이상한 자료형의 향연  
줄바꿈도 이상하고, 이상한 플래그도 있다.

![코드예3-2]()  
-> 메서드 추출, 이름 변경, 구조 변경
: 훨씬 더 읽기 좋고 이해가 쉬움  

## 작게 만들어라

`함수는 첫째도 작게, 둘째도 작게`  
80년대에는 한 함수가한화면을 넘어서는 안되었다 ( 80자*24줄 )  

얼마나 짧게?  

`3-2`는 아래의 `3-3`만큼 줄어야한다.  
![코드예3-3]()  

## 블록과 들여쓰기

`if문/else문/while문 등에 들어가는 블록은 한 줄이어야 한다`  
왜냐하면, 대체로 함수를 호출하는 부분이기 때문이다.  
바꿔말하면, 함수의 들여쓰기 수준을 1~2단으로 유지하란 말이다.  
이를 통해 함수는 더욱 더 읽고 이해하기 쉬워진다.  

## 한가지만 해라

`함수는 한가지를 해야하고, 그 한가지를 잘해야하며, 그 한가지만을 해야한다` - TODO원어가 궁금함.

`3-1`에선

1. 버퍼 생성
2. 페이지 가져오기
3. 상속 페이지 검색
4. 경로 랜더링
5. 문자열 붙이기
6. HTML생성

등을 하는 반면, `3-3`은 한 가지만 처리한다  

그렇다면, '한가지'의 기준은 무엇인가?

우선 `3-3`의 코드가 한가지가 맞는가?  

1. isTestPage - 테스트 페이지 여부 체크
2. includeSetupAndTeardownPages - 1에서 true면 설정페이지와 해제페이지를 넣는다.
3. pageData.getHTML - 페이지를 HTML로 랜더링

이렇게 나열하면, `3-3`은 세가지인가? 한가지인가?  
위에서 언급하는 세가지는 지정된 함수 이름 아래에서 추상화 수준이 하나.  
함수는 간단한 TO<sup>[3](#3)</sup>문단으로 기술할 수 있다.

> TO: RenderPageWithSetupsAndTearDowns, 페이지가 테스트 페이지인지 확인한 후 테스트 페이지라면 설정 페이지와 해제 페이지를 넣는다. 테스트 페이지든 아니든 페이지를 HTML로 렌더링한다.

우리가 함수를 만드는 이유는 큰개념(시스템)을 단계적인 추상화를 통하여 단계적 수행을 하기 위해서이다.

따라서, 한가지만 하는 함수란 `추상화 수준이 하나인 단계만 수행하는 함수`라고 할 수 있다.

추상화 수준이 하나라면, 의미 있는 이름으로 다른 함수를 추출할 수 없을 것이고, 추출할 수 있다면 그 함수는 여러 작업을 하는 샘이다.`[G34]` & `p90_4-7/generatePrime/declarations,initalizations,sieve`

TODO `3-1`, `3-2`도 TO문을 작성해보기

---

## 함수 당 추상화 수준은 하나로

`함수 내 모든 문장의 추상화 수준이 같아야 한다`

`3-1`에서의 추상화 수준 정리

```java
public void example () {
  String pagePathName = "abc";

}
```

의 추상화 수준 중간
