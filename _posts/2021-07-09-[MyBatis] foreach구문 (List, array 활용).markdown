---
layout: post
title:  "[MyBatis] foreach구문 (List, array 활용)"
date:   2021-07-09 21:56:03 +0900
categories: jekyll update
---
21.07.09.

<br>

## 문제

프로젝트를 진행하며 반복적으로 데이터값을 바꿔 넣으며 sql문 실행이 필요한 경우가 발생하여, for문, while문 없이 MyBatis 내에서 실행 가능한 코드구현 필요   

<br>

## 해결

반복적으로 데이터값을 바꿔 넣으며 sql문 실행이 필요한 경우   
파라미터로 List 또는 array 를 넣고, <foreach> 구문을 활용한다.   


```xml
<select id="memCart" parameterType="ArrayList" resultType="com.spring.model.ProductDTO">
	select * from product where pro_no in
	<foreach collection="list" item="item" open="(" close=")" separator=",">#{item.value}</foreach>
</select>
```

<br>

---
참고 | [[MyBatis] foreach 구문, parameterType List, Model, Map 사용](https://linked2ev.github.io/mybatis/2020/01/05/MyBatis-5-foreach-%EA%B5%AC%EB%AC%B8,-parameterType-List-Model-Map/)