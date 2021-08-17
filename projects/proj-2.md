---
layout: post
title: "Spring project : 울퉁불퉁's"
---
<p style="font-size:13px">* 이미지 클릭시 원본 크기로 열람가능합니다.</p>

#### Subject
<center><img src="../assets/img/projects/proj-2/logo2.png" style="text-align:center; cursor: pointer;" onclick="window.open(this.src)"></center>

> 농산물 구독사이트 **울퉁불퉁's**

충분히 맛있지만 흠집이 있거나 생산량이 많다는 이유만으로 버려지는 농산물을 합리적인 가격으로 판매하는 인터넷 쇼핑몰을 구독방식과 결합하여 구현.

코로나로 인해 침체된 농가에 활력을 불어넣고 일반적으로 상품가치가 없다고 여겨지는 농산품에 새로운 가치를 부여하자는 프로젝트.

<br> 

---
#### Tools

<p align="center"><img src="../assets/img/projects/proj-2/27.png" style="cursor: pointer;" onclick="window.open(this.src)"></p>


<br>

---
#### Design

<img src="../assets/img/projects/proj-2/28.png" style="cursor: pointer;" onclick="window.open(this.src)">

* brand
	- **울퉁불퉁's** : 못난이 채소의 연상이 자연스럽고 어감이 귀여운 '울퉁불퉁' + Spring project의 'S'
	- 대표 이미지 컬러 : 신선하면서도 시인성이 좋은 <span style="color:#FF8F1C;">#FF8F1C</span> <span style="color:#ABD037;">#ABD037</span>

* references
	- [freshshop](https://technext.github.io/freshshop/about.html) \| [ogani](https://technext.github.io/ogani/checkout.html) \| [freshugly](https://www.freshugly.com/)


<br>

---

#### Project
* github : [울퉁불퉁's 프로젝트](https://github.com/csooy38/SpringTeamProject)
* notion : [프로젝트 진행상황](https://url.kr/y2l6c8) \| [이슈](https://url.kr/xfab7e)

<br>

---
#### DataBase

<img src="../assets/img/projects/proj-2/29.png" style="cursor: pointer;" onclick="window.open(this.src)">

- Oracle DB(RDS)
- 크게 회원/상품/결제 테이블로 나누어서 구성.
- 회원 아이디를 주 외래키로 사용하여 review, qna, like, coupon 테이블 연결, cascade delete 설정.
- 결제 테이블은 주문번호를 외래키로 사용하여 주된 주문정보(주문인, 주문정보, 쿠폰, 총액 등)와 주문된 상품정보를 연결.

<br>

---
#### 담당 업무
<img src="../assets/img/projects/proj-2/30.png" style="cursor: pointer;" onclick="window.open(this.src)">

* 전체적인 프로젝트의 병합 관리(git).

* 프론트 작업
	- 상품관련 모든 페이지(상품리스트, 상품상세, 상품검색, 장바구니)와 관리자 페이지(상품등록, 수정, 삭제, 카테고리 등록 수정 삭제)를 담당. 반응형 웹까지 모두 구현.
	- 그외 팝업창 등 부분적으로 css 작업.

<br>

* 구현 기능
	- RESTful api 를 사용하여 SNS(네이버, 카카오)로 로그인, 회원가입 기능 구현.
	- 상품 관련 CRUD, Q&A CRUD, 카테고리 CRUD, 세션에 따른 노출여부 구현.
	- 찜하기, 장바구니 수량변경 Ajax로 실시간 DB 반영. 세션으로 로그인 회원을 조회하여 적용.
	- 상품 등록, 수정시 CKEditor 를 사용하여 이미지 편집 및 유투브 삽입 가능하도록 구현.
	- 비회원인 경우 일부 기능(찜하기, Q&A작성 등) 사용시 팝업창으로 로그인 유도.
	- 그외 마이페이지 주문내역, daum 지도 api를 사용한 주소 등록, 관리자 회원 관리 등의 기능구현에 기여.

<br>

---
#### View
최대 1200px, 768px, 576px 3가지 뷰포트를 나누어서 반응형 적용. 

- <b>반응형 - 태블릿 PC (max-width: 768px)</b>
<center><img src="../assets/img/projects/proj-2/76802.gif" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>반응형 - 모바일 (max-width: 576px)</b>
<center><img src="../assets/img/projects/proj-2/56802.gif" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Main</b>
<center><img src="../assets/img/projects/proj-2/00.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Login & Join</b>
	- 네이버/카카오로 로그인 가능
	- daum api로 주소 조회
<center><img src="../assets/img/projects/proj-2/23.png" style="width: 45%; box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"> <img src="../assets/img/projects/proj-2/24.png" style="width:45%; box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>About</b>
<center><img src="../assets/img/projects/proj-2/01.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Product List</b>
	- 상품별 찜하기 기능
<center><img src="../assets/img/projects/proj-2/02.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Product Detail</b>
<center><img src="../assets/img/projects/proj-2/03.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Product Detail - review</b>
<center><img src="../assets/img/projects/proj-2/04.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Product Detail - Q&A</b>
<center><img src="../assets/img/projects/proj-2/05.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>
<center><img src="../assets/img/projects/proj-2/25.png" style="width:45%; box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"> <img src="../assets/img/projects/proj-2/26.png" style="width:45%; box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Cart</b>
<center><img src="../assets/img/projects/proj-2/06.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Purchase</b>
	- 카카오페이로 결제
<center><img src="../assets/img/projects/proj-2/07.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Search List</b>
	- 상단바 또는 태그 클릭으로 검색
<center><img src="../assets/img/projects/proj-2/08.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>My Page</b>
<center><img src="../assets/img/projects/proj-2/09.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Admin Page - member list</b>
<center><img src="../assets/img/projects/proj-2/16.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Admin Page - product list</b>
<center><img src="../assets/img/projects/proj-2/17.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Admin Page - product create</b>
<center><img src="../assets/img/projects/proj-2/21.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Admin Page - product update</b>
<center><img src="../assets/img/projects/proj-2/20.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

- <b>Admin Page - category</b>
<center><img src="../assets/img/projects/proj-2/22.png" style="box-shadow: 3px 3px 10px; cursor: pointer;" onclick="window.open(this.src)"></center><br>

<br>


<br>
