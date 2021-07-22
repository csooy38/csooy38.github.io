---
layout: post
title:  "[JSP] Cannot convert [y] of type [class java.lang.String] to [class java.lang.Long]"
subtitle: 간단한 형변환 오류
date:   2021-07-12 10:32:03 +0900
categories: jekyll update
tags: [jsp]
---

<br>

## ❓ 문제

<p align="center"><img src="../assets/img/images/210722/01.png"></p>

```java
javax.el.ELException: Cannot convert [y] of type [class java.lang.String] to [class java.lang.Long]
	at org.apache.el.lang.ELSupport.coerceToNumber(ELSupport.java:395)
	at org.apache.el.lang.ELSupport.coerceToNumber(ELSupport.java:374)
```

상품 검색 중 다른 탭은 괜찮은데 유독 판매상태만 검색하면 오류가 발생했다.  
그것도 판매상태가 아니라 엉뚱하게도 카테고리 코드에서.  

<br>

---
## ❕ 해결

찬찬히 뜯어보니 판매상태는 String 값으로 데이터가 넘어가는 반면 카테고리는 int 값으로 데이터를 저장하고 있었다.  
그러다보니 검색 후 keyword를 불러올 때 String을 int와 비교하는 문제가 발생한 것.  
찾아보니 **EL 태그는 기본적으로 String 타입**이라는 것도 한 몫 한 거 같았다.

int 값을 String.valueOf 으로 형변환해주면서 간단하게 해결했다.  


이 부분을

```html
<c:if test="${keyword eq dto.getCate_no() }">selected</c:if>
```
<br>

이렇게 수정

```html
<c:if test="${keyword eq String.valueOf(dto.getCate_no()) }">selected</c:if>
```

<br>

---

반대의 경우엔 오류가 발생하지 않았다.  
EL태그는 기본적으로 String 타입이기 때문이다.

| [참고] [참고페이지](https://docs.oracle.com/cd/E17802_01/products/products/jsp/jstl/1.1/docs/tlddocs/index.html)



