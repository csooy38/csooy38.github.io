---
layout: post
title:  "[MyBatis] There is no getter for property named 'no' in 'class java.lang.Integer' 에러"
subtitle: mapper에서 if문 작성시 String 형변환이 불가능하다는 에러
date:   2021-07-22 14:43:03 +0900
categories: jekyll update
tags: [mybatis, error]
---

<br>

## ❓ 문제

```xml
<select id="productTotalRecord" resultType="int">
	select count(*) from product where pro_check = 'y' 
	<if test="no gt 0"> and pro_category = #{no}</if> 
</select>
```

product.mapper에서 위와 같이 작성했더니 자꾸 getter 가 없다는 오류가 발생했다.  
if문을 지우고 실행하면 제대로 동작하는 걸 보니 파라미터 자체의 오류는 아닌 것처럼 보였다.  

<br>

```xml
There is no getter for property named 'no' in 'class java.lang.Integer'
```

그동안 숱하게 int 타입을 파라미터로 넘겨왔건만  
새삼스럽게 오류가 나니 황당 그 자체였다.  

<br>

---
## ❕ 해결

언제나 그렇듯 원인은 간단하다.  
**MyBatis의 조건절에서는 인자값을 parameterType의 클래스로부터 getter 메서드를 이용해 가져오기 때문** 이다.  
애초에 Integer 클래스엔 getter 메서드가 존재하지 않으므로 오류가 발생하게 된 것.  

결국 getter 메서드가 있는 HashMap으로 묶어준 후에야 해결되었다.  

if문뿐만 아니라 where문 등 다른 조건절에서도 동일하게 오류가 난다고 하니 기억해두자! 


이 부분을

```java
int no = 값;
totalRecord = this.pdao.getProductListCount(no);
```
<br>

이렇게 수정

```java
int no = 값;
HashMap<String, Integer> hm = new HashMap<String, Integer>();
hm.put("no", no);

totalRecord = this.pdao.getProductListCount(hm);
```

<br>

참고로 파라미터명 대신 value 로 작성해도 동작한다고 한다.  

```xml
<select id="productTotalRecord" resultType="int">
	select count(*) from product where pro_check = 'y' 
	<if test="value gt 0"> and pro_category = #{value}</if> 
</select>
```

실험 결과 value 로도 잘 작동했다.  
굳이 map으로 한 번 더 감싸거나 DTO 객체를 만들 필요 없이  
그냥 value 를 쓰는 게 가장 효율적이겠다.  

<br>

---
| [참고] [[MyBatis] There is no getter for property named.. error](https://marobiana.tistory.com/24) <br/>
| [참고] [(mybatis) There is no getter for property named 'no' in 'class java.lang.String' 에러](https://blog.naver.com/0192141606/70173329588)



