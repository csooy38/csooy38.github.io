---
layout: post
title:  "[Annotation] 애노테이션"
date:   2021-06-18 17:55:00 +0900
categories: jekyll update
---
21.06.18.

<br>

# Annotation

> 스프링 애노테이션(annotation).   
> 천천히 추가 중.

<br>

---
## 1. 설정 방법
1. pom.xml 에 라이브러리 추가
	1. <a href="http://mvnrepository.com">mvnrepository.com</a> - 애노테이션 이름 search 
	2. 버전에 맞는 라이브러리 선택 - Maven 코드 복사
	3. pom.xml 파일에서 <dependency> 태그들 사이에 붙여넣기
	4. 필요한 클래스 상단에 애노테이션(`@`) 추가

<br>
	
---
### * Lombok 
1. 추가방법
	* 방법 1
		1. <a href="http://projectlombok.org/download">projectlombok.org/download</a> - Download 1.18.20
		2. 다운로드 받은 파일 실행 - Specify Location - 스프링 설치 경로(sts.exe) 설정 - install/update - Quit Installer

	* 방법 2
		* pom.xml 에 라이브러리 추가

		```xml
		<!-- lombok 라이브러리 -->
		<dependency>
			<groupId>org.projectlombok</groupId>
			<artifactId>lombok</artifactId>
			<version>1.18.20</version>
			<scope>provided</scope>
		</dependency>
		```

2. 종류

	```java
	@Data			// getter/setter
	@NoArgsConstructor	// 인자를 가지지 않는 생성자
	@AllArgsConstructor	// 모든 멤버를 인자로 가지는 인자생성자
	```

<br>

---
### * cglib

1. 애노테이션 역할
	* 컴파일러에게 정보를 알려주는 역할.
	* 컴파일 할 때와 설치 시의 작업을 지정하는 역할.
	* 실행할 때에 별도의 처리가 필요한 경우 사용되는 역할.


2. 추가방법 : pom.xml에 cglib 라이브러리 추가.

	```xml
	<!-- cglib 라이브러리 : 동적으로 자바 클래스의 프록시를 생성해주는 기능 제공 -->
	<dependency>
	    <groupId>cglib</groupId>
	    <artifactId>cglib</artifactId>
	    <version>2.2.2</version>
	</dependency>
	```

3. 종류

	```java
	@Configuration	// 클래스 앞에 선언하는 애노테이션. "해당 클래스는 스프링 설정에 사용되는 클래스입니다."라고 알려주는 애노테이션.
	@bean 		// 메소드 앞에 사용되는 애노테이션. "해당 메서드는 객체를 생성하는데 사용됩니다." 의미.
	```
<br>

---
### * spring-jdbc

```xml
<!-- https://mvnrepository.com/artifact/org.springframework/spring-jdbc -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
    <version>${org.springframeword-version}</version>
</dependency>
```

<br>

---
### * c3p0

```xml
<!-- c3p0 라이브러리 -->
<dependency>
	<groupId>com.mchange</groupId>
	<artifactId>c3p0</artifactId>
	<version>0.9.5.2</version>
</dependency>
```

<br>

---
### * `@Repository`
Spring에서 일반적으로 DAO 클래스에 적용되는 애노테이션.

<br>

---
### * `@Autowired`
자동으로 의존관계가 설정되는 애노테이션.    
무조건 객체에 대한 의존을 주입하는 애노테이션.  

<br>

---
### * aspectjweaver

```xml
<!-- Spring AOP aspectjweaver 라이브러리 -->
<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjweaver</artifactId>
    <version>1.9.6</version>
</dependency>
```

<br>

---
### * MyBatis

* mybatis 프레임워크 라이브러리

```xml
<!-- mybatis 프레임워크 라이브러리 -->
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis</artifactId>
    <version>3.4.6</version>
</dependency>
```

<br>
	
* mybatis-spring 라이브러리

```xml
<!-- mybatis-spring 라이브러리 -->
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis-spring</artifactId>
    <version>1.3.2</version>
</dependency>
```

<br>

* spring-jdbc 라이브러리
	
```xml
<!-- spring-jdbc 라이브러리 -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
    <version>${org.springframework-version}</version>
</dependency>
```

<br>

---
### * 파일 업로드 관련

* commons-fileupload(Apache Commons FileUpload)

```xml
<!-- https://mvnrepository.com/artifact/commons-fileupload/commons-fileupload -->
<dependency>
    <groupId>commons-fileupload</groupId>
    <artifactId>commons-fileupload</artifactId>
    <version>1.3.1</version>
</dependency>
```

<br>

* Apache Commons IO 도 함께 사용하기도 한다.

```xml
<!-- https://mvnrepository.com/artifact/commons-io/commons-io -->
<dependency>
    <groupId>commons-io</groupId>
    <artifactId>commons-io</artifactId>
    <version>2.4</version>
</dependency>
```


