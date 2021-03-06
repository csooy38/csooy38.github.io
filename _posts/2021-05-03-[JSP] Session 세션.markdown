---
layout: post
title:  "[JSP] Session"
date:   2021-05-03 18:33:35 +0900
categories: jekyll update
tags: [jsp, session]
---
# JSP
---

# Session 세션
- 쿠키와 마찬가지로 서버와의 connection 관계를 유지하기 위해서 이용자
        정보를 저장하는 객체임.

<br>

## 1. 세션의 특징
- 세션은 서버에서만 접근이 가능함. - 서버의 메모리에 저장됨.
- 쿠키보다 보안성이 높음.
- 서버에 부하를 줄 수 있음.
- 쿠키의 기본 용량이 4KB, 300개로 제한적인 반면에 세션은 데이터에 제한이 없음.
- 브라우저당 한 개의 세션이 생성이 됨.
- 세션은 유효 시간을 가짐. - 기본 유효 시간은 30분임.
- 로그인 상태 유지 기능이나 쇼핑몰의 장바구니 담기 기능 등에 주로 사용이 됨.
  
<br>

---
## 2. 세션 관련 메서드
- setAttribute() : 세션의 속성을 설정하는 메서드.
	* 형식) session.setAttribute("id", value);
- getAttribute() : 세션에서 데이터를 얻어올 때(세션에 속성을 사용할 때) 이용하는 메서드.
	* 형식) String id = (String)session.getAttribute("id");
- getAttributeNames() : 세션에 저정되어 있는 모든 데이터의 이름을 얻어올 때 사용하는 메서드. 
- removeAttribute() : 세션의 특정 데이터를 제거하는 메서드.
	* 형식) session.removeAttribute("id");
- invalidate() : 세션의 모든 데이터를 삭제하는 메서드. 
- getId() : 자동 생성된 세션의 아이디를 얻어올 때 사용하는 메서드.
- isNew() : 세션이 최초로 생성되었는지 여부를 알고자 할 때 사용하는 메서드.
- getMaxInactiveInterval() : 세션의 유효 시간을 얻어을 때 사용하는 메서드.