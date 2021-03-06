# jpabook
## ๐ ํ๋ก์ ํธ ๋ชฉ์ 
JPA ๊ธฐ๋ณธ ๊ฐ์ ๊ด๋ จ ์ฐ์ต ํ๋ก์ ํธ
<br/>

## Language
<img src="https://img.shields.io/badge/Java-blue?style=flat-squar"/>

## Technology
<img src="https://img.shields.io/badge/H2-FFCA28?style=flat-squar"/>

## IDEA
<img src="https://img.shields.io/badge/IntelliJ IDEA-6A5FBB?style=flat-square&logo=IntelliJ IDEA&logoColor=white"/>

## Maven์ ์ด์ฉํ JPA ์ธํ (persistence.xml)


```java

<!-- ํ์ ์์ฑ -->
<property name="javax.persistence.jdbc.driver" value="org.h2.Driver"/>
<property name="javax.persistence.jdbc.user" value="sa"/>
<property name="javax.persistence.jdbc.password" value=""/>
<property name="javax.persistence.jdbc.url" value="jdbc:h2:tcp://localhost/~/test"/>
<property name="hibernate.dialect" value="org.hibernate.dialect.H2Dialect"/>


<!-- ์ต์ -->
<property name="hibernate.show_sql" value="true"/>
<property name="hibernate.format_sql" value="true"/>
<property name="hibernate.use_sql_comments" value="true"/>
<property name="hibernate.hbm2ddl.auto" value="create" />

```
## H2 Database๋?
>์ฃผ์ ๊ธฐ๋ฅ
* ๋น ๋ฅด๊ณ  ์คํ์์ค์ธ JDBC API
* In Memory DB(์ธ ๋ฉ๋ชจ๋ฆฌ DB)
* Embedded mode(๋ด์ฅ๋ชจ๋) & Server mode(์๋ฒ๋ชจ๋) ์ง์
* ๋ธ๋ผ์ฐ์  ๊ธฐ๋ฐ ์ฝ์ ํ๋ก๊ทธ๋จ
* 2MB์ ๋์ ์ ์ ์ฉ๋์ผ๋ก ์ค์น ๊ฐ๋ฅ
* ANSI ํ์ค SQL๋ก ์ฌ๋ฌ ํธํ์ฑ ๋ชจ๋ ์ง์(DB2, Derby, HSQLDB, MS SQL Server, MySQL, Oracle, PostgreSQL, Ignite)
<br/>

> Embedded Mode vs Server Mode
* Embedded mode(๋ด์ฅ๋ชจ๋) : Application ์๋ฒ ์คํ ์ข๋ฃ์ ๋ฐ์ดํฐ ๋ชจ๋ ํ๋ฐ
* H2๋ฅผ Application๊ณผ ๋์ผํ JVM์ ์ด์ฉํ์ฌ ๊ตฌ๋, Application์ด ์ข๋ฃ๋๋ฉด Data๊ฐ ๋ชจ๋ ์์ค(ํ๋ฐ) - ์์์ ์ด์ง ์์
* ํ์คํธ ์ฝ๋ ์คํ์ ํ๋ฐ์ฑ์ผ๋ก ๋์์ํค๋ ๊ฒฝ์ฐ๊ฐ ๋ง์ผ๋ฏ๋ก ํด๋น ๋ชจ๋๋ฅผ ์ฌ์ฉํจ

* Server mode(์๋ฒ๋ชจ๋) : Application ์๋ฒ ์ข๋ฃ์์๋ ์ง์์ ์ผ๋ก ํด๋น ๋ฐ์ดํฐ๋ฅผ ์ฌ์ฉ
* ๋ณ๋์ JVM์ ์ด์ฉํ์ฌ ๊ตฌ๋ (localhost:9092) - ์์์ ์ผ๋ก ์ฌ์ฉํ  ์ ์์
* ์ฌ๋ฌ Application์ด ํด๋น H2์ ๋์ ์ ๊ทผ ๊ฐ๋ฅ
* Application๊ณผ๋ TCP/IP ํต์ 
<br/>

> H2๋ฅผ ์ ํํ ์ด์ 
* ๊ฐ๋ณ๊ณ  ์ค์น๊ฐ ์ฝ๊ณ , ๊ด๋ฆฌ๊ฐ ํธํ๋ค
* SQL๋ก ์ฌ๋ฌ ํธํ์ฑ ๋ชจ๋ ์ง์์ด ๊ฐ๋ฅํ๋ค

## ์ฃผ์ ์ต์
* hibernate.show_sql, hibernate.format_sql, use_sql_comments: ์ฝ์ ์ฐฝ์ JPA ์ฟผ๋ฆฌ๋ฅผ ๊น๋ํ๊ฒ ์ถ๋ ฅํ๊ธฐ ์ํด ์ฌ์ฉ
* hibernate.hbm2ddl.auto: ํ๋ก๊ทธ๋จ์ ๋๋ฆด๋ DDL์ ์ด๋ป๊ฒ ํ ์ง ์ํ (clear๋ก ์๋ ฅํ ๊ฒฝ์ฐ ๊ธฐ์กด DB๋ฅผ ๋ค drop์ํค๊ณ  ์๋ก ๋ง๋ฌ)

## ERD ์ค๊ณ
>๋๋ฉ์ธ ์ค๊ณ
<img width="80%" src="https://user-images.githubusercontent.com/46039671/178140653-60c10e1a-ceee-4218-885d-fe0218e83e5b.png"/>
<br/>
<br/>

>๋๋ฉ์ธ ์ค๊ณ ์์ธ
<img width="80%" src="https://user-images.githubusercontent.com/46039671/178140645-3c93bae4-753e-498a-8749-b0002ce5fc4b.png"/>
<br/>
<br/>

>ํ์ด๋ธ ์ค๊ณ
<img width="80%" src="https://user-images.githubusercontent.com/46039671/178140654-8225d28e-8c5b-4a14-8ec6-6bfd735dc8ae.png"/>
