---
layout: post
title:  "[JSP] Action Tag"
date:   2021-05-03 18:33:36 +0900
categories: jekyll update
tags: [jsp]
---
# JSP
---

# ActionTag 액션태그
- 페이지 내에서 어떤 동작을 하도록 지시하는 태그.
	* 예) 페이지 이동(forward), 페이지 포함(include), param
- 웹 컨테이너에서 실행되고 결과만 웹 브라우저에 전달되어 출력.
- 자바 빈(bean)과 연관이 있는 태그.
  
<br>

## 1. 액션태그의 종류
- 표준 액션(standard action) : JSP 페이지에서 바로 사용할 수 있는 액션. 
- 커스텀 액션(custom action) : 별도의 라이브러리를 설치해서 사용하는 액션.
  
  
- 표준 액션 사용 예)

```jsp
    <jsp:include page="a.jsp">
```
* jsp 접두어는 표준 액션을 의미한다.