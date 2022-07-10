# jpabook
## 👋 JPA 기본 강의 관련 실전 연습 프로젝트
JPA 기본 강의 관련 연습 프로젝트
<br/>

## 사용 DB
<img src="https://img.shields.io/badge/H2-FFCA28?style=flat-squar"/>

## Maven을 이용한 JPA 세팅 (persistence.xml)


```java

<!-- 필수 속성 -->
<property name="javax.persistence.jdbc.driver" value="org.h2.Driver"/>
<property name="javax.persistence.jdbc.user" value="sa"/>
<property name="javax.persistence.jdbc.password" value=""/>
<property name="javax.persistence.jdbc.url" value="jdbc:h2:tcp://localhost/~/test"/>
<property name="hibernate.dialect" value="org.hibernate.dialect.H2Dialect"/>


<!-- 옵션 -->
<property name="hibernate.show_sql" value="true"/>
<property name="hibernate.format_sql" value="true"/>
<property name="hibernate.use_sql_comments" value="true"/>
<property name="hibernate.hbm2ddl.auto" value="create" />

```
## H2 Database란?
>주요 기능
* 빠르고 오픈소스인 JDBC API
* In Memory DB(인 메모리 DB)
* Embedded mode(내장모드) & Server mode(서버모드) 지원
* 브라우저 기반 콘솔 프로그램
* 2MB정도의 적은 용량으로 설치 가능
* ANSI 표준 SQL로 여러 호환성 모드 지원(DB2, Derby, HSQLDB, MS SQL Server, MySQL, Oracle, PostgreSQL, Ignite)
<br/>

> Embedded Mode vs Server Mode
* Embedded mode(내장모드) : Application 서버 실행 종료시 데이터 모두 휘발
* H2를 Application과 동일한 JVM을 이용하여 구동, Application이 종료되면 Data가 모두 손실(휘발) - 영속적이지 않음
* 테스트 코드 실행시 휘발성으로 동작시키는 경우가 많으므로 해당 모드를 사용함

* Server mode(서버모드) : Application 서버 종료시에도 지속적으로 해당 데이터를 사용
* 별도의 JVM을 이용하여 구동 (localhost:9092) - 영속적으로 사용할 수 있음
* 여러 Application이 해당 H2에 동시 접근 가능
* Application과는 TCP/IP 통신
<br/>

> H2를 선택한 이유
* 가볍고 설치가 쉽고, 관리가 편하다
* SQL로 여러 호환성 모드 지원이 가능하다

## 주요 옵션
* hibernate.show_sql, hibernate.format_sql, use_sql_comments: 콘솔 창에 JPA 쿼리를 깔끔하게 출력하기 위해 사용
* hibernate.hbm2ddl.auto: 프로그램을 돌릴때 DDL을 어떻게 할지 셋팅 (clear로 입력할경우 기존 DB를 다 drop시키고 새로 만듬)

## DB 설계
>도메인 설계
<img width="80%" src="https://user-images.githubusercontent.com/46039671/178140653-60c10e1a-ceee-4218-885d-fe0218e83e5b.png"/>
<br/>
<br/>

>도메인 설계 상세
<img width="80%" src="https://user-images.githubusercontent.com/46039671/178140645-3c93bae4-753e-498a-8749-b0002ce5fc4b.png"/>
<br/>
<br/>

>테이블 설계
<img width="80%" src="https://user-images.githubusercontent.com/46039671/178140654-8225d28e-8c5b-4a14-8ec6-6bfd735dc8ae.png"/>
