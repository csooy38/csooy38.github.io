---
layout: post
title:  "[MyBatis] foreach 구문 방식 여러 가지"
subtitle: MyBatis 에서의 insert, update 구문 반복, foreach 구문에서 selectKey 값 증가시키기
date:   2021-09-25 06:32:03 +0900
categories: jekyll update
tags: [mybatis]
---

<br>

## 1. foreach 구문 - insert

foreach 구문에 **open="INSERT ALL" close="SELECT * FROM DUAL"** 추가  

foreach 구문 안에서 반복되며 순차적으로 증가해야 하는 컬럼이 있다면  
**#{INFO_IDX, jdbcType=VARCHAR} + To_NUMBER(#{index})** 로 처리  

```xml
<insert id="insertInfo" parameterType="hashmap">
	<selectKey resultType="string" keyProperty="INFO_IDX" order="BEFORE">
		SELECT NVL(MAX(INFO_IDX) + 1, 1) FROM INFO
	</selectKey> 
	<foreach item="item" index="index" collection="list" open="INSERT ALL" close="SELECT * FROM DUAL">
		INTO INFO(
			  INFO_IDX
			, NAME
			, REGIST
			, GENDER
			, REGDATE
		) VALUES (
			  #{INFO_IDX, jdbcType=VARCHAR} + To_NUMBER(#{index})
			, #{item.NAME, jdbcType=VARCHAR}
			, #{item.REGIST, jdbcType=VARCHAR}
			, #{item.GENDER, jdbcType=VARCHAR}
			, SYSDATE
		)
	</foreach>
</insert>
```

<br>

---
## 2.  foreach 구문 - update

foreach 구문 안에 **open="DECLARE BEGIN" close="; END;" separator=";"** 추가  

```xml
<update id="updateInfo" parameterType="hashmap" >
	<foreach collection="list" item="item" open="DECLARE BEGIN" close="; END;" separator=";">
		UPDATE INFO
		SET 
			  NAME = #{item.NAME, jdbcType=VARCHAR}
			, GENDER = #{item.GENDER, jdbcType=VARCHAR}
			, REGIST = #{item.REGIST, jdbcType=VARCHAR}
			, REGDATE = TO_DATE(#{item.REGDATE, jdbcType=VARCHAR}, 'YYYY-MM-DD HH24:MI:SS')
			, UPDDATE = SYSDATE
		WHERE 
			INFO_IDX = #{item.INFO_IDX}
	</foreach>
</update>
```

<br>

---
참고 | [[MyBatis] List 파라메터 foreach 사용 (INSERT, DELETE, MERGE, UPDATE) - Oracle](https://haenny.tistory.com/21)   

