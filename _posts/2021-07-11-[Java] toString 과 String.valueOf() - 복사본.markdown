---
layout: post
title:  "[Java] toString() 과 String.valueOf()"
date:   2021-07-11 21:56:03 +0900
categories: jekyll update
---
21.07.11.

<br>

# toString() 과 String.valueOf()

둘의 차이는 명확하다.   

<br>

들어오는 값이 없을 때
`toString()`은 NullPointerException을 발생시키는 반면,   
`String.valueOf()`은 null 이라는 문자열을 생성하여 저장한다.  

