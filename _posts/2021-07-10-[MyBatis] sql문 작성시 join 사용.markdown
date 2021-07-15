---
layout: post
title:  "[MyBatis] sql문 작성시 join 사용"
date:   2021-07-10 21:56:03 +0900
categories: jekyll update
tags: [mybatis]
---
## 문제

sql문 작성시 join을 사용하여    
PRODUCT와 PRODUCT_RECENT 테이블의 모든 데이터를 가져오려고 하는데    
resultType 지정이 곤란한 상황 발생하였다.   

하나의 DTO만으로는 두 테이블의 데이터를 담지 못하고,    
하나의 DTO에 다른 테이블의 DTO를 멤버변수로 선언하자니 변수가 중복되고 지저분해질 거 같았다.  

<br>

---
## 해결

resultType이 아니라 resultMap 을 사용하여 join한 데이터를 모두 받아온다.

1) dto에 join할 테이블에 해당하는 클래스를 멤버로 선언한다.  

```java
@Data
public class ProductRecentDTO {

	private int recent_no; // 기존 멤버
	
	private ProductDTO productDTO; // join될 테이블
}
```

<br>

2) mapper에서 <resultMap>으로 두 클래스를 모두 선언한다.   

이 때 join할 테이블의 속성 중 <collection>에 join될 테이블을 넣는다.
<collection property="" resultMap=" join될 테이블 resultMap의 id ">

```xml
<resultMap type="com.spring.model.ProductDTO" id="product"> <!-- join될 테이블 -->
		<result column="pro_no" property="pro_no" />
		<result column="pro_name" property="pro_name" />
</resultMap>

<resultMap type="com.spring.model.ProductRecentDTO" id="recent">
		<result column="recent_no" property="recent_no" />  <!-- 기존 멤버 -->
		<collection property="productDTO" resultMap="product" /> <!-- join될 테이블 -->
</resultMap>
		
<select id="recentList" parameterType="String" resultMap="recent">
		select *
		from product p join product_recent r
		on p.pro_no = r.recent_product
		where r.recent_mem = #{id}
		order by r.recent_regdate desc
</select>
```

<br>

뷰페이지에선 다음과 같이 출력하면 된다.

기존 멤버는 그대로, join된 멤버는 클래스를 불러온 후 getter로 가져온다.

```html
${dto.getRecent_no() } <!-- 기존 -->
${dto.getProductDTO().getPro_no() } <!-- join된 테이블 -->
```

사용자체는 두 테이블의 외래키를 활용하여 데이터를 가져오기 위함이다 보니  
[[MyBatis] foreach구문 (List, array 활용)](https://www.notion.so/MyBatis-foreach-List-array-939d277d2e084e179fc997267b52bd07) 와 결과는 동일하다. 
단지 mapper 하나로 정리하느냐, 컨트롤러를 오가며 list 를 만들어 넘기느냐의 차이가 있을 뿐이다. 

<br>

---
참고 | [mybatis resultMap 활용 - join](https://ssssssu12.tistory.com/4)

