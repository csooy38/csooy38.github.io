---
layout: post
title:  "[Java] String, StringBuilder, StringBuffer"
date:   2021-07-11 21:56:03 +0900
categories: jekyll update
---
21.07.11.

<br>

# String, StringBuilder, StringBuffer

---
## 1. String과 StringBuilder, StringBuffer의 차이   
`String`은 동일한 변수명이더라도 값이 변할 때마다 **새로운 주소값**을 가지는 반면,   
`StringBuilder`와 `StringBuffer`는 동일한 변수명은 **동일한 주소값**을 유지한다.  

<br>

예를 들어 `String` 변수 a의 값을 "test1"에 "test2"를 추가하면   
아래와 같이 110251487 에서 110251488로 해시코드가 변한 것을 볼 수 있다.   

```java
String a = "test1";
System.out.println("test1 >> " + a.hashCode());

a += "test2";
System.out.println("test2 >> " + a.hashCode());

결과)
test1 >> 110251487
test2 >> 110251488
```

<br>

반면에 `StringBuilder`로 변수 생성 후 동일한 테스트를 진행하면   
처음 가진 주소값 1510467688이 그대로 유지되는 걸 볼 수 있다.  

```java
StringBuilder b = new StringBuilder();
b.append("test1");
System.out.println("test1 >> " + b.hashCode());

b.append("test2");
System.out.println("test2 >> " + b.hashCode());

결과)
test1 >> 1510467688
test2 >> 1510467688
```

<br>

이러한 차이는 어디에서 오는 걸까?   

`String`에 저장되는 문자열은 `private final char` 타입으로 저장된다.    
즉, 한 번 선언된 문자열은 외부에서 접근이 불가능하며, 바꿀 수도 없는 상수로 처리된다.    
따라서 동일한 변수에 문자열을 추가하여도 접근조차 불가능하여 새로운 주소값을 할당받을 수밖에 없는 것이다.    

<br>

반면에 `StringBuilder`와 `StringBuffer`는 `private final`의 제약조건이 없기 때문에 동일한 변수의 주소값 내에서 문자열의 변화가 자유롭다.   
`String`은 기본적인 문자열 타입으로 사용하기 무척 쉽고 유용하지만,    
메모리 관리 측면에서 보자면 주소값이 반복적으로 쌓여 비효율적이라고도 할 수 있겠다.    

<br>

---
## 2. StringBuilder와 StringBuffer

그렇다면 `StringBuilder`와 `StringBuffer`의 차이는 무엇일까?

<br>

multi thread 환경에서   
`StringBuilder`에는 thread들이 동시에 접근이 가능하지만,   
`StringBuffer`는 synchronization이 적용되어 다른 값을 변경할 수 없어 안전하다고 한다.  

<br>

---
참고 | [Java에서 String, StringBuilder, StringBuffer의 차이](https://novemberde.github.io/2017/04/15/String_0.html)

