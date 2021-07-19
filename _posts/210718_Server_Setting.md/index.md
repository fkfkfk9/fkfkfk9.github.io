---
title: CentOS7 톰켓 셋팅
date: 2021-07-18 23:33:33
tags: [서버, Tomcat, Mysql]
categories: [서버, Tomcat, Mysql]
---

# CentOS7 톰켓 셋팅

1. wget를 설치한다.  
   ![](1.yum%20업데이트.png)
2. net-tools를 설치한다.(ifconfig)  
   ![](2.yum업데이트%20수락.png)
3. gcc gcc-c++설치한다. (컴파일)  
   ![](3.wget설치.png)
4. mysql 그룹, 계정 추가 및 mysql 다운로드  
   ![](4.mysql%20다운로드.png)
5. gz압축을 푼다.  
   ![](5.mysql설치.png)
6. 압축푼 경로로 들어간다.  
   ![](6.mysql서버%20설치.png)
7. 옆에 코드를 입력 ./configure --prefix=/usr/local/mysql --localstatedir=/usr/local/mysql/data --sysconfdir=/etc --with-mysqld-ldflags=-all-static --with-client-ldflags=-all-static --without-debug --enable-assembler --with-charset=utf8 --with-plugins=innobase --with-extra-charsets=all  
   ![](7.mysql서버%20시작.png)
8. No curses/termcap library found 오류가 발생 시 옆에걸 설치하고 다시 한다. yum install libtermcap-devel ncurses-devel  
   ![](8.mysql%20초기암호%20확인법.png)
9. make / make install 입력해준다.  
   ![](9.mysql%20초기셋팅.png)
10. cp ./support-files/my-medium.cnf /etc/my.cnf 파일 이동(오버라이트 옵션이 뜬다면 y를 눌러준다.  
    ![](10.비밀번호%20셋팅완료..png)
11. /usr/local/mysql/bin/mysql_install_db 입력해준다.  
    ![](11.각종%20권한설정.png)
12. chown -R mysql.mysql /usr/local/mysql/data mysql계정에 권한부여  
    ![](12.mysql설치완료%20후%20접속..png)
13. cp support-files/mysql.server /usr/local/mysql/bin
    chmod 755 /usr/local/mysql/bin/mysql.server
    /usr/local/mysql/bin/mysql.server start 입력
    스타트 파일을 복사하고 권한주소 서버를 시작한다.  
    ![](13.mysql%20user추가.png)
14. /usr/local/mysql/bin/mysqladmin -u root password '원하는대로' 여기서 패스워드 설정을 한다.  
    ![](14.mysql%20user권한추가.png)
15. mysql을 실행시키고 로그인한다.  
    ![](15.mysql%20변경저장%20및%20방화벽%20포트추가.png)
16. pkill mysqld
