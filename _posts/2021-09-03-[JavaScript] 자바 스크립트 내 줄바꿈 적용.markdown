---
layout: post
title:  "[JavaScript] 자바 스크립트 문자열 내 줄바꿈 적용"
subtitle: 하나의 문자열 내 줄바꿈 적용하기
date:   2021-09-03 07:51:03 +0900
categories: jekyll update
tags: [javascript]
---

<br>

## 1. 역슬래시(\) 이용하는 방법
- 개행문자(\) 반복 작성 필요
- 들여쓰기시 그대로 적용됨

```javascript
console.log("First Line\
	Second Line\
	Third Line")
```

<br>

출력)
```html
First LIne
	Second Line
	Third Line
```

<br>

---

## 2. 역따옴표( ` ) 이용하는 방법
- 처음과 끝에만 개행문자를 작성하면 됨
- 들여쓰기기 그대로 적용됨

```javascript
console.log(`First Line
Second Line
Third Line`)
```
<br>

출력)
```html
First LIne
	Second Line
	Third Line
```

<br>

* 두 방법 모두 들여쓰기가 그대로 적용되므로 주의

<br>

---

## 3. 적당한 방법
- 개행문자를 직접 작성해야 함
- 들여쓰기 그대로 적용 X

```javascript
console.log("First Line\n" +
	"Second Line\n" +
	"Third Line")
```

<br>

출력)
```html
First LIne
Second Line
Third Line
```

<br>

---

참고 \| [[javascript] 여러 줄 문자열](https://itholic.github.io/js-multiline-string/)
