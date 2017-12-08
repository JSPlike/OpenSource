MySQL REFERENCE MANUAL
===================

## **0. MySQL 개요**

### 왜 MySQL인가?
데이터베이스는 데이터를 일정한 형태로 저장해 놓은 것을 의미한다. 하지만 단순 파일에 데이터를 일괄적으로 저장하는 것과는 많은 차이가 있다. 단순 파일과는 다른  많은 기능들이 데이터베이스 내에 존재하며 이러한 기능들은 데이터를 보다 정밀하게 조작해야 하는 일에 유용하게 사용될 수 있다. 웹 애플리케이션을 만들거나 서버와 클라이언트를 이용한 프로그램을 제작해야 하는 경우, 데이터베이스를 이용해 체계적으로 구축한 데이터는 더욱 더 그 가치를 발휘할 수 있다.
#### 
4차 산업시대인 현재, 대량의 데이터를 효율적으로 관리하는 것은 더 중요한 것으로 여겨지고 있다. 이러한 사회의 흐름에서 프로그래머라면 누구나 한 번쯤은 관심을 가질 수밖에 없는 데이터베이스 분야 중 가장 접근하기 편한 데이터베이스는 MySQL일 것이다. 오픈소스이고 무료로 제공된다는 점에서도 충분히 매력있지만 이식성이 좋고 가볍고 빠르다는 점에서 많은 웹 애플리케이션은 기본 데이터베이스로 MySQL로 채택하고 있다.
#### 
이러한 의식의 흐름에서 보다 많은 사람들이 MySQL을 쉽고 편하게 사용할 수 있도록 한글 매뉴얼을 제작해보고자 MySQL이라는 오픈소스를 선택하게 되었다. 문서는 데이터베이스 관리 시스템과 그중 하나인 MySQL을 소개하는 것부터 이를 컴퓨터에 설치하고 SQL언어로 데이터를 직접 조작하는 방법까지 차례로 기술되었다. 구체적인 목차는 아래와 같다.
#### 

[TOC]


## **1. DBMS와 MySQL 소개**
-------------
### 1-1 DBMS
**데이터베이스 관리 시스템(DBMS)**[^dbms]은 다수의 사용자들이 데이터베이스 내의 데이터를 접근할 수 있도록 해주는 소프트웨어 도구의 집합이다. 또한 DBMS은 사용자 또는 다른 프로그램의 요구를 처리하고 적절히 응답하여 데이터를 사용할 수 있도록 해준다.

DBMS는 크게 6가지의 기능을 가지고 있다.
>**Note:**

> - 정의 : 데이터에 대한 형식, 구조, 제약조건들을 명세하는 기능이다. 이때 데이터베이스에 대한 정의 및 설명은 카탈로그나 사전의 형태로 저장된다.
> - 구축 : DBMS가 관리하는 기억 장치에 데이터를 저장하는 기능이다.
> - 조작 : 특정한 데이터를 검색하기 위한 질의, 데이터베이스의 갱신, 보고서 생성 기능 등을 포함한다.
> - 공유 : 여러 사용자와 프로그램이 데이터베이스에 동시에 접근하도록 하는 기능이다.
> - 보호 : 하드웨어나 소프트웨어의 오동작 또는 권한이 없는 악의적인 접근으로부터 시스템을 보호한다.
> - 유지보수 : 시간이 지남에 따라 변화하는 요구사항을 반영할 수 있도록 하는 기능이다.


----------


### 1-2 MySQL
 **MySQL**[^mysql]은 DBMS중 관계형 데이터베이스 관리 시스템(RDBMS)에 분류되는 시스템이다. 또한 MySQL은 페이스북, 구글, 어도비등 세계에서 가장 규모가 크고 빠르게 성장하는 기업들에서 사용되고 있는 관계형 데이터베이스 관리 시스템(RDBMS)이기도 하다. 기업들은 이 시스템을 사용하여 대용량 웹 사이트, 비즈니스 크리티컬 시스템 및 패키지 소프트웨어에 전력을 공급하고 시간을 절약한다.

MySQL은 표준 데이터베이스 질의언어인 SQL(Structured Query Language)를 사용하는 개방소스의 관계형 데이터베이스 관리 시스템이다. 그리고 속도가 빠르면서 가볍고 유연하기 때문에 초보자도 쉽게 다룰 수 있는 쉬운 인터페이스인 것이 특징이다.

MySQL은 데이터베이스를 따로 관리하기 위한  GUI (Graphical User Interface)관리 툴이 내장되어 있지가 않다. 그렇기 때문에 이용자들은 데이터베이스를 만들거나 관리, 백업, 상태 검사, 레코드 삽입 등의 작업을 할 때에 명령 줄 인터페이스도구, MySQL 프론트엔드 데스크톱 소프트웨어, 혹은 웹 애플리케이션을 사용해야 한다.


----------


### 1-3 MySQL 구조
![mysql구조사진](http://cfile28.uf.tistory.com/image/26219B435902D8852210A8)

위 사진은 MySQL의 아키텍쳐를 나타낸다. 사진을 보면 MySQL이 Storage Engines와 SQL Interface, Optimizer, Parser등을 구분하고 있는 것을 볼 수 있다. MySQL의 서버는 두가지 크게 두개의 엔진으로 구분되어 지는데 첫번째는 **MySQL엔진**, 그리고 두번째는 **Storage 엔진**이다. 이 둘의 특징은 다음과 같다.


>**MySql Engine**
>
> - MySQL 엔진은 클라이언트로부터 접속 및 쿼리 요청을 처리하는 커넥션 핸들러와 SQL 파서 및 전처리기, 그리고 쿼리의 최적화된 실행을 위한 옵티마이저가 중심을 이룬다. 그리고 성능 향상을 위해 MyISAM의 키 캐시나 InnoDB의 버퍼 풀과 같은 보조 저장소 기능이 포함되어 있다. 또한, MySQL은 표준 SQL(ANSI SQL-92) 문법을 지원하기 때문에 표준 문법에 따라 작성된 쿼리는 타 DBMS와 호환되어 실행될 수 있다.



>**Storage Engine**
>
> - MySQL 엔진은 DBMS의 두뇌 역할을 담당하며 요청된 SQL 문장을 분석하거나 최적화하는 등의 처리를 수행한다. 그리고 스토리지 엔진은 실제 데이터를 디스크 스토리지에 저장하거나 디스크 스토리지로부터 데이터를 읽어오는 부분을 수행한다.
> - MySQL 서버에서 MySQL 엔진은 한 개만 존재하는 반면 스토리지 엔진은 여러 개를 동시에 사용할 수 있다. 예를 들어, 테이블이 사용할 스토리지 엔진을 지정하면 이후 해당 테이블의 모든 읽기 작업이나 변경 작업은 정의된 스토리지 엔진이 처리하게 된다.	


----------


### 1-4 실습환경

>**환경:**
>
> - Ubuntu 16.04 LTS
> - MySQL 5.7.20
> - Apache 2.0
> - PHP 7.1
	 

	
 > **Tip:** 무작정 최신버전을 설치하는 것은 좋지 않다. 
	 

----------


## **2. MySQL 설치하기**


### 2-1 가상머신에 Ubuntu 설치

#### 2-1-1 **Windows 환경**

**VMware** 가상머신의 설치:

먼저 VMware라는 가상머신 소프트웨어를 다운받는다.

 <https://www.vmware.com/>
 
 위의 주소로 들어간다.

아래의 사진은 VMware사이트의 메인 화면

![vmware install_01](http://cfile26.uf.tistory.com/image/99AC13335A237B2521D607)

왼쪽 사이드바의 **다운로드** 부분으로 들어간다.


![vmware install_02](http://cfile28.uf.tistory.com/image/99378A335A237B270848E6)

위와 같이 여러가지 종류의 가상머신 버전이 존재한다. 우리는 개인용 컴퓨터에서 사용할 예정이므로 Personal Desktop 탭에서 VMware Workstation Player을 무료로 다운받는다.

#### 2-1-1 **Mac 환경**


> TIP :
> 
> Mac에서는 가상머신을 사용하기위해 parallels라는 앱을 사용한다. 이 앱은 본래 parallels홈페이지에서 유료로 다운받아 사용해야 했지만 **parallels Lite**의 출시 이후, linux관련 OS는 모두 무료로 사용할 수 있게 되었다.


##### **(1) parallels 검색**

**parallels Lite**의 설치는 AppStore에서 가능하다. 먼저 Mac에서 SpotLight를 실행한 뒤, App Store를 검색한다.

![spotlight 검색](http://cfile27.uf.tistory.com/image/992413335A2380551C0E59)

##### **(2) parallels 설치**

App Store에서 parallels Lite를 검색한 뒤 설치한다.

![parallels lite 검색](http://cfile22.uf.tistory.com/image/9945B2335A23808E269378) 

##### **(3) app 실행**

설치가 되셨다면 앱을 실행한다. 앱에서는 윈도우관련 운영체제는 유료로 제공하지만 리눅스 운영체제는 전부 무료로 제공하고 있다.

![앱 실행](http://cfile8.uf.tistory.com/image/998A0B335A23813724B6B7)

##### **(4) 우분투 설치**

우분투 설치는 아주 간단하다. 우분투 앱을 더블 클릭한 뒤 다운로드 버튼을 누르기만 하면 간단히 OS가 설치된다.

![우분투 다운](http://cfile22.uf.tistory.com/image/99418A335A23821820145A)

----------
### 2-2 MySQL 설치
#### **2-2-1 Windows 환경**
##### **(1) 설치**
mysql을 설치하는 방법에는 여러가지가 있지만 그 중 간편하게 설치하는 방법으로 APMSETUP이 있다.

	APMSETUP 이라고 하는 사이트에 접속하여 다운로드 페이지로 들어간다.

참고로 APM은 Apache Php Mysql의 약자이다. 이 프로그램을 설치하게 되면 컴퓨터에 Apache, PHP, mysql이 모두 설치가 되며 복잡한 설정을 할 필요가 없이 여러 시스템들을 사용할 수 있다

	[APMSETUP7 DOWNLOAD] 를 클릭하여 파일을 다운로드 받는다.

	실행한다.

언어 설정을 하고
다음다음다음 약관 확인
APM_Setup 7 Default Data를 선택하고 다음
설치 폴더 지정한 후 설치
방화벽 엑세스 허용한 후 마침

*README 파일* 에서 설치된 프로그램들의 버전을 확인할 수 있다.

------
##### **(2) 설치 확인**

잘 설치 되었는지 확인하기 위해 웹 브라우저에 localhost를 입력해 본다.

별도의 설정이 필요한 경우 표시된 설정 파일 경로에 있는 설정파일을 수정하면 된다.

cmd 창 접속 후

	mysql -uroot -p [enter]
	apmsetup [enter]

초기 비밀번호는 apmsetup이다. 하지만 필수적으로 비밀번호 변경하는 것을 권장한다.

	mysql> show databases;

위의 명령으로 데이터 베이스의 목록을 확인할 수 있다.

-----
##### **(3) 웹기반의 mysql 클라이언트인 phpMyadmin 접속 방법**


hp 작업 표시줄의 아이콘 중 APMSETUP아이콘을 오른쪽 버튼으로 클릭한 후 mysql관리를 클릭한다.

	사용자명: root
	비밀번호: apmsetup

라고 입력한 뒤  실행을 누른다.
 
phpMyadmin은 mysql과 관련된 거의 모든 작업을 할 수 있는 강력한 프로그램으로 실행을 하면 데이터베이스 리스트를 볼 수 있다.
데이터 베이스를 클릭하면 해당 데이터베이스에 존재하는 테이블 리스트를 확인할 수 있다.

----
##### **(4) uroot 비밀번호 변경방법**

tray에서 apmsetup moniter라고 하는 이 시스템 tray를 오른쪽 클릭 후 mysql root 패스워드 변경을 클릭하고 패스워드를 변경한다.

-------
>※ 참고
>Apache phpMyadmin과 같은 시스템들은 윈도우보다는 리눅스를 선호하기 때문에 여유가 된다면 가상머신을 이용하여 리눅스를 설치하고 그 위에 mysql을 설치하는 것을 권장한다.



#### **2-2-2 Mac 환경**
##### **(1) 설치**
**# MAMP Stack**
 
Mac에서 MySQL을 설치하는 방법은 여러가지가 있다. 이 문서에서는 그중 bitnami에서 제공하는 MAMP Stack이라는 것으로 MySQL을 설치하는 방법을 알아볼 것이다.
##### 
**Bitnami MAMP Stack**은 완전 통합형이며 MAMP 개발 환경을 제공합니다. PHP, MySQL 및 Apache 외에도 FastCGI, OpenSSL, phpMyAdmin, ModSecurity, SQLite, Varnish, ImageMagick, xDebug, Xcache, OpenLDAP, ModSecurity, Memcache, OAuth, PEAR, PECL, APC, GD, cURL 및 기타 구성 요소가 포함됩니다. Zend Framework, Symfony, CodeIgniter, CakePHP, Smarty, Laravel과 같은 프레임 워크등을 제공하고 있다.

---------

>**Note:**
>MAC에서 bitnami MAMP Stack을 이용한 설치 방법 이외에도 Homebrew를 이용하여 쉽게 설치하는 방법도 있다. 시간이 된다면 Homebrew를 이용해 MySQL을 설치하는 방법도 익혀보면 좋을 것이다.

MAMP Stack을 다운받기 위해 먼저 bitnami사이트에 들어간다.

>**[ MAMP Stack 설치 ]**

><https://bitnami.com/stack/mamp>

>위의 링크를 통해 binami 사이트에 접속해보자 처음 접속하게 되면 이런 화면을 볼 수 있다. MAMP의 간단한 설명이 나와있다. 이 글의 위 내용이 있을 것이다.  
#### 
![mamp](http://cfile4.uf.tistory.com/image/99282B335A27F86C0ED112)
#### 
	 
 **MAMP**의 설치를 위해 오른쪽  **LOCAL INTALL**탭의 버전을 선택해 다운로드를 받아준다. 여기서는 현재의 최신버전인 **7.1.12.0 버전**을 설치할 것이다. 링크를 클릭하면 아래의 화면이 보이면서 설치가 완료된다.
#### 
![install end](http://cfile29.uf.tistory.com/image/997996335A27F88B0604E7)

이제 MAMP를 실행해 봅시다.


<img src="http://cfile6.uf.tistory.com/image/99DAF8335A27F985206DE9" width="400px" height="350px">


다운이 완료되었다면 Mac의 응용프로그램에 들어가서 MAMP를 실행할 수 있다. 더블클릭을 하는 것 만으로 MAMP설치 프로그램을 실행한다.

실행프로그램이 시작되면 몇가지 설정을 할 수 있는 화면들이 보이게 된다. 이때 설정이 필요없는 부분은 그냥 Pass하고 phpmyadmin등이 체크되어 있는 체크박스가 보인다.
#### 
<img src="http://cfile7.uf.tistory.com/image/9917BD335A27FA0C0DB923" width="600px" height="400px">

>**Note**
>MAMP를 설치하게 되면 기본으로 apache2와 PhpMyAdmin이 같이 설치되어진다. 이점을 유의해야 한다.

MySQL, Apache2, PHP 등과 관련이 없는 체크항목은 모두 체크해제를 하고 Next버튼을 진행해준다.
#### 
<img src="http://cfile5.uf.tistory.com/image/992FC5335A27FA6C3408CE" width="600px" height="400px">

MAMP Stack의 경로설정까지도 그냥 디폴트 경로로 이용하고 Next 버튼을 눌러 설치를 진행해준다.


>**Note**
>설치시 비밀번호를 입력하라는 폼이 등장한다. 이때 설정한 비밀번호는 나중에 MySQL접속시 루트계정의 비밀번호로 사용되니 외워두자.

##### **(2) manager-OSX**

설치가 완료되었다면 이제 Mysql을 실행해보자.

	실제로 여기까진 진행하였다면 MySQL의 설치는 완료된 것이다. 이제 MySQL실행하고 중지하는 manager-OSX를 알아보자.

Mac의 응용프로그램을 담고 있는 Lanchpad에 들어가서 **manager-OSX** 프로그램을 실행해봅시다.

<img src="http://cfile6.uf.tistory.com/image/9968CA335A27FB27335991" width="600px" height="400px">

세개의 탭중 **Manage Servers** 탭에서 MySQL Database를 Start, Stop할 수 있다. MySQL 뿐만아니라 아파치 웹 서버도 여기서 쉽게 제어할 수 있다.

	MySQL Database는 Start하고 아파치 웹서버는 Stop하여 사용을 중지해준다. 굳이 아파치 웹 서버를 지금 사용하지 않을 것이기 때문이다.

##### **(3) MySQL 접속**

이제  MySQL에 접속이 되어지는지 확인해보아야 한다. 터미널에 들어가 다음의 명령어들을 수행해야 한다.

MySQL 실행기가 있는 곳까지 가기위해 이 명령을 실행해야한다.


![이동](http://cfile25.uf.tistory.com/image/99602D335A27FC80324778)

	cd /Applications/mampstack-7.1.12-0[버전은 다를 수 있다]/mysql/bin

그후 MySQL 접속 명령어를 입력하고 엔터를 누른다

	./mysql -uroot -p

이제 비밀번호를 입력하는 화면이 뜰 것이고 아까 등록한 비밀번호를 입력해준다.

![mysql 접속](http://cfile28.uf.tistory.com/image/99A4C4335A27FD5F0E2D75)

Welcome이라는 글씨가 보이면서 **mysql >** 의 입력란이 보이면 설치에 성공한 것이다. 

#### **2-2-3 Linux 환경**
##### **(1) 설치**
리눅스 중 우분투(Ubuntu)라고 하는 리눅스 배포판을 설치했다고 가정한 후의 설명이다.
#### 
terminal 창을 열고  아래의 명령어를 작성한다.

[ Apache 설치 ]

	sudo apt-get install apache2

[ mysql 설치 ]

	sudo apt-get install mysql-server mysql-client


[ php 설치 ]

	sudo apt-get install php5-common php5 libapache2-mod-php5

[ php-mysql 연동 모듈 설치 ]

	sudo apt-get install php5-mysql


[ 아파치 재 시작 ]

	sudo /etc/init.d/apache2 restart

만약 mysql만 설치할 것이라면 mysql만을 설치하면 된다.
###### 
하지만 일반적으로 mysql이 웹을 위해 많이 사용되기도 하고 웹 환경에서 가장 많이 사용되는 기술 중 하나가 아파치라는 웹 서버와 php라고 하는 미들웨어이기 때문에 일반적으로 mysql, php, apache는 함께 사용되는 경우가 많다.

-----------
모두 설치하였으면 terminal 창에 다음과 같이 입력하여 mysql에 접속한다.

	mysql -uroot -p [enter]
	[password 입력]

mysql -uroot -p [password] 의 방법으로 접속하는 것 또한 가능하지만 보안을 고려하여 엔터 이후 password를 입력하는 것이 더 좋다.
### 
	show databases;

를 입력하면 현재 존재하는 database리스트가 보인다.

-------
##### **(2) 설치 확인**

**"apache가 잘 설치되었는지 확인**하기 위해서는 firefox의 주소창에 localhost를 입력하여 접속해본다.
##### 
It works! 가 출력되는 화면으로 접속할 것이다. 부가적인 확인을 위해 아래의 과정을 참고한다. 아래의 과정은 index.html이라는 파일이 현재 웹브라우저에서 localhost를 입력할 때 출력하고 있다는 것을 보이기 위한 과정으로 생략해도 좋다.

	cd /var/www/index

/var/www/index 경로로 들어간 후

	ls -al

파일 목록을 조회하면 index.html 파일을 확인할 수 있다.

	cat index.html

이 파일을 열람해본다.


	vim index.html

이 파일을 에디터에서 오픈하여 It works! 라는 문자열을 수정해본다.

---------
**"php가 잘 설치되었는지 확인**하기 위한 과정은 다음과 같다.

/var/www/index 경로에서

	sudo vi phpinfo.php

위 명령을 사용하여 vi 에디터로 phpinfo.php라는 이름의 파일을 하나 생성한다.
#### 
i를 눌러 삽입모드로 변경한 다음 아래 내용을 작성한 후 :wq 와 엔터를 눌러 위의 내용을 저장한다.


	< ?
	phpinfo();
	? >




firefox에서 주소 창에 localhost/phpinfo.php를 입력하며 접속하면 php와 관련된 다양한 환경에 대한 내용들이 출력된다.
##### 
이 내용들이 잘 출력되면 php가 잘 설치되었다는 의미이고 내용을 확인하다 보면 mysql에 관한 내용도 있는 것을 볼 수 있을 것이다. 이는 mysql이 php와 잘 연동되었다는 의미이다.

----------
#### 2-3 MySQL 클라이언트(Client)
저장된 데이터를 서버가 제공한 기능들을 이용하여 핸들링 하는 것을 데이터베이스 클라이언트라고 한다. 클라이언트가 웹으로 치면 서버가 웹 서버이고 데이터베이스 클라이언트는 웹 브라우저와 같은 기능을 한다고 할 수 있다.
mysql의 클라이언트는 아주 많은 **종류**가 있다. 그 중 대표적인 것로는 다음과 같다.


- **mysql-moniter**
mysql을 설치하면 기본적으로 함께 설치되는 프로그램으로  mysql에서 만든 회사에서 제공하는 오픈소스 프로그램으로 무료로 사용 가능하다. 콘솔 환경에서 사용하는 명령어 기반의 클라이언트이다.

- **mysql query browser**
이 프로그램 또한 마찬가지로 mysql을 만든 회사에서 제공하는 프로그램이다. 이 프로그램은 기본적으로 설치되는 것은 아니기 때문에 사용하려면 [여기](http://dev.mysql.com/downloads/gui-tools/5.0.html,)에서 별도로 다운로드 해야 한다. GUI(Graphic User Interface)환경이기 때문에 데이터베이스를 쉽게 접근할 수 있다는 장점이 있다.


- **phpMyAdmin**
서버에 직접 설치되어 있는 웹 프로그램이다. mysql-moniter나 mysql query browser와 같은 경우는 개인 컴퓨터에 설치되어 있을 때만 사용 가능한 반면 phpMyAdmin은 웹으로 제공되는 서비스이기 때문에 장소에 제한되지 않고 웹 환경에서 데이터베이스를 제어할 수 있어 편리하다는 장점이 있다. phpMyAdmin에 대한 더 자세한 정보는 [여기](http://www.phpmyadmin.net/home_page/index.php)에서 볼 수 있다.

- **navicat**
navicate은 아주 많은 기능이 있고 안정적인 클라이언트 프로그램이다. 유료 프로그램이고 가격이 비싸지만 그 만큼 편리하고 가치 있는 프로그램이라고 할 수 있다. navicat은 [여기](http://www.navicat.com)에서 다운로드 할 수 있다.

- **그 밖의 클라이언트**
'TOAD' 에 대한 정보를 보려면 [클릭](http://www.quest.com/toad-for-mysql/)
'올챙이' 에 대한 정보를 보려면 [클릭](https://sites.google.com/site/tadpolefordb/)

----------


## **3. MySQL  실습하기**

### 3-1 MySQL 실행

**"MySQL을 실행**하는 것은 간단하다. 터미널을 열고 `$mysql -uroot -p` 를 입력 한 후 엔터를 친 뒤 아까 설정한 MySQL의 암호를 입력하면 된다. MySQL에 들어가면 버전정보, 설치날짜등을 볼 수 있고 새로운 입력 창이 뜨는 것을 확인할 수 있다.

[사진 부분]

	
먼저, MySQL에 현재 어떠한 데이터베이스들이 있는지 확인하기위해
 `>> show databases;` 입력해본다.

[사진 부분]

### 
#### 3-1-1 Database
**"Database**란 데이터가 실질적으로 적재되는 테이블들을 분류하는 상위 개념을 말한다.


##### (1) 데이터베이스 생성
SQL 명령어를 이용하여 데이터베이스를 생성하는 명령어는 다음과 같다.

	CREATE DATABASE `데이터베이스명` CHARACTER SET utf8 COLLATE utf8_general_ci;

여기서 데이터베이스명 양쪽에 붙어있는 기호 **`**은 작은따옴표가 아니라 **억음부호(grave accent)**라고 하는 것으로 키보드 상으로는 아래 그림과 같은 위치에 있다.

[그림]

그리고 `CHARACTER SET utf8 COLLATE utf8_general_ci` 은 특정 데이터베이스의 인코딩 설정을 하는 명령으로 현재 생성할 데이터베이스의 기본 언어 인코딩 값을 UTF-8로 설정한다는 의미이다. 인코딩이 무엇인지 잘 모를 때에는 위와 같이 쓰는 것이 바람직하다.

--------
아래의 query문을 사용하여 임의의 데이터베이스 class를 생성해본다.

	CREATE DATABASE `class` CHARACTER SET utf8 COLLATE utf8_general_ci;

#### 
`show databases;` 명령어로 데이터베이스를 확인해보면 아래와 같은 결과가 나타날 것이다.

[그림]

--------
##### (2) 데이터베이스 삭제

데이터베이스를 삭제하는 query문은 다음과 같다.

	DROP DATABASE `데이터베이스명`;
만약 위에서 만들었던 class라는 데이터를 삭제하기 위해 **DROP DATABASE \`class\`;**라는 명령어를 사용한다면 class 데이터베이스가 사라지는 것을 확인할 수 있을 것이다.

----- 
##### (3) 데이터베이스 열람

데이터베이스를 열람하기 위한 query문은 다음과 같다.

	SHOW DATABASES;

------
##### (4) 데이터베이스 선택

위의 명령어로 어떠한 데이터베이스가 존재하는 지 확인했다면 특정 데이터베이스에 들어가 데이터 작업을 할 수 있어야 한다. 특정 데이터베이스를 선택하는 query문은 아래와 같다.

	USE `데이터베이스명`;


----------

#### **※ 실습 준비**

실습에 사용한 샘플을 다운로드 하고 싶다면 [클릭](http://ttend.tistory.com/604)		
   		
**[source 파일경로]**를 통해서 테이블을 데이터베이스에 저장한다.		
####  		 
![테이블 샘플 다운로드](http://cfile29.uf.tistory.com/image/2732B542587610BF2395B7)		
  		
저장된 테이블을 확인한다.		
#### 		
![테이블 확인](http://cfile23.uf.tistory.com/image/2159FE3E587610DF159D9D)		

---------

#### **SQL의 분류**


SQL의 쿼리 명령어는 크게 DDS, DML, DCL 3가지로 분류할 수 있다.

	1. DDL(Data Define Language : 데이터 정의어) : CREATE, ALTER, DROP

	→ SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의, 변경, 삭제 할 때 사용하는 언어
	
	2. DML(Data Manipulation Language : 데이터 조작어) : INSERT, DELETE, UPDATE, SELECT
	→ 데이터베이스 사용자가 응용 프로그램이나 질의어를 통하여 저장된 데이터를 실질적으로 처리하는 데 사용되는 언어

	3. DCL(Data Control Language : 데이터 제어어) : COMMIT, ROLLBACK, GRANT, REVOKE
	→ 데이터의 보안, 무결성, 회복, 병행 수행 제어 등을 정의하는 데 사용되는 언어


---------

### **3-2 DDL**
#### 3-2-1 CREATE

##### (1) **"테이블(Table)** 이란
'데이터가 실질적으로 저장되는 저장소' 라고 할 수 있다.
비유하자면 데이터베이스가 디렉토리라고 할 때 테이블은 파일이라고 할 수 있다.
디렉토리는 파일들을 그룹핑해주는 역할을 하는 것이고 파일은 데이터를 담는 역할을 한다. 여기서 파일과 유사한 기능을 하는 것이 **테이블**이라고 할 수 있다.
## 

##### (2) **"스키마(schema)**란?

테이블에 적재될 데이터의 구조와 형식을 정의 하는 것을 말한다.
테이블에 어떤 형식의 데이터들이 삽입되고 저장될 것인지는 데이터를 삽입하기 전에 미리 정의 해놓아야 한다.
###### 
즉, 스키마는 일종의 데이터의 설계도라고 할 수 있다. 만약 스키마와 맞지 않는 데이터를 삽입하려고 하면 오류가 발생한다.

##### 
##### (3) **테이블 생성**
테이블을 생성하는 쿼리문은 아래와 같다.
>-> SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의
>**CREATE TABLE 테이블명(  **
>   **컬럼명 데이터타입**
>**);**

--------------------- 
 - 예제   

	-- student 테이블 생성
	
		CREATE TABLE `student` (
		    `id`  tinyint NOT NULL ,
		    `name`  char(4) NOT NULL ,
		    `sex`  enum('남자','여자') NOT NULL ,
		    `address`  varchar(50) NOT NULL ,
		    `birthday`  datetime NOT NULL ,
		    PRIMARY KEY (`id`)
		);
    -- BONUS 테이블 생성

		CREATE TABLE IF NOT EXISTS `BONUS` (
		  `ENAME` varchar(10) DEFAULT NULL,
		  `JOB` varchar(9) DEFAULT NULL,
		  `SAL` double DEFAULT NULL,
		  `COMM` double DEFAULT NULL
		) ENGINE=InnoDB DEFAULT CHARSET=utf8;

 BONUS 의 이름을 가진 테이블에 ENAME, JOB, SAL, COMM의 column을 가진 테이블을 생성

 
##### 

IF NOT EXISTS는 존재하지 않을 경우를 뜻함. 즉 **CREATE TABLE IF NOT EXISTS**는 테이블이 존재하지 않을 경우 생성하라는 의미. 추가옵션으로 필요로 할시에 사용한다.
 
##### 

-------
테이블을 생성할 때 사용하는 **데이터 타입**과 **제약조건**은 다음과 같다. 
#### 
##### (4) **"데이터 타입**

|Data Type | Explanation |
| :---------- | :--------- |
| CHAR   |  0 ~ 255 고정문자 길이      |
| VARCHAR | 0 ~ 65535 가변 문자 길이 (테이블을 만들 때 문자의 길이를 20으로 지정하여도 삽입시 문자의 길이가 5만큼의 크기를 차지 했을 때 5만 차지하도록 해준다)|
| INT | -2147483648 ~ 2147483647 정수형|
| FLOAE | 작은 부동소수점|
| DOUBLE | 큰 부동소수점|
|DECIMAL(M, D) | 소수부의 자릿수를 미리 정해 놓고, 고정된 자릿수로만 소수 부분을 표현 ` M : 소수 부분을 포함한 실수의 총 자릿수 / 최댓값 65, D : 소수 부분의 자릿수, D가 0이면 정수`|
| DATE | YYYY-MM-DD (년-월-일)|
| DATETIME | YYYY-MM-DD HH:MM:SS (년-월-일 시:분:초)|
| TIMESTAMP | YYYYMMDDHHMMSS (년월일시분초)|
| TIME | HH:MM:SS (시:분:초)|

##### 

##### (5) **"제약조건**      

|Constraint | Explanation |
| :---------- | :--------- |
| NOT NULL | 해당 column은 NULL로 지정할 수 없다.|
| UNIQUE | 해당 column은 서로 다른 값을 가진다.|
| PRIMARY KEY | NOT NULL + UNIQUE, 대표키로 값에 NULL을 넣을 수 없고 식별할 수 있는 값을 넣어야만 한다. 반드시 1개 이상 명시.|
| FOREIGN KEY | 테이블간에 연관성을 갖도록 하고 \``참조 무결성"을 명시 |
| CHECK| 애트리뷰트나 도메인 정의 뒤에 사용하여 데이터의 값을 제한할 수 있다. -> 투플 기반 제약 조건  ex)\`SAL\` double DEFAULT NULL CHECK ( \`SAL\`>0 AND \`SAL\`<5000)|


--------------
**[제약조건 문법]**
  
  
| Constraint  | 예시 (Create문 안에 쓴다고 가정)                                                                          |
|-------------|-----------------------------------------------------------------------------------------------------------|
| NOT NULL    | 컬럼명 데이터형 NOT NULL → ID INT NOT NULL                                                                |
| UNIQUE      | UNIQUE(컬럼명) → UNIQUE(ID)                                                                               |
| PRIMARY KEY | PRIMARY KEY(컬럼명) → PRIMARY KEY(ID)                                                                     |
| FOREIGN KEY | FOREIGN KEY(컬렴명) REFERENCES 테이블명 (참조할 컬럼명) → FOREIGN KEY(ssn) REFERENCES EMPLOYEE(Super_ssn) |
| CHECK       | 컬럼명 데이터형 CHECK(조건) → SAL double CHECK ( SAL>0 AND SAL<5000)|                                     |


--------------

##### (6) **``참조 무결성**이란?
한 테이블의 레코드는 반드시 다른 테이블의 레코드와 연관시켜야 하는 것을 의미한다. 레코드를 삽입, 삭제, 수정할 때 참조 무결성 제약조건에 위배될 수 있기 때문에 유의해야 한다.
##### 
참조무결성이 위반되는 경우 아래와 같이 **해결**한다.

>	 1) Default operation 
>		 >\`SAL\` double NOT NULL DEFAULT 1000;
		 
>	 2) referential triggered action 절
 
>> **FOREIGN KEY(Super_ssn) REFERENCES EMPLOYEE(ssn)**

> **ON DELETE SET NULL ON UPDATE CASCADE** 

 > (ssn이 삭제되면 Super_ssn을 NULL로 설정, ssn이 수정되면 Super_ssn도 수정된 값으로 변경)
 > or
 > **ON DELETE SET DEFAULT ON UPDATE CASCADE**
 > (DEFAULT는 UPDATE, DELETE에선 NULL과 같은 의미)


----------
#### 3-2-2 ALTER

ALTER 쿼리문은 TABLE에 대한 정의를 변경하는 역할을 한다.
명령어의 사용 방법은 아래와 같다.

	ALTER TABLE 테이블명 ADD 추가할컬럼명 데이터형
	ALTER TABLE 테이블명 MODIFY 변경할컬럼명 데이터형
	ALTER TABLE 테이블명 DROP 삭제할컬럼명
### 

---------
##### (1) 테이블에 있는 컬럼 수정, 추가, 삭제하기  
<img src="https://github.com/JSPlike/OpenSource/blob/gaeun/5.JPG?raw=true" width="600px" height="400px">
<img src="https://github.com/JSPlike/OpenSource/blob/gaeun/6.JPG?raw=true" width="600px" height="400px">
<img src="https://github.com/JSPlike/OpenSource/blob/gaeun/7.JPG?raw=true" width="600px" height="400px">

##### (2) 테이블에 제약조건 추가하기  
<img src="https://github.com/JSPlike/OpenSource/blob/gaeun/10.JPG?raw=true" width="600px" height="400px">



-----------
#### 3-2-3 DROP
DROP 쿼리문은 SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 삭제하는 역할을 한다.
명령어의 사용방법은 아래와 같다.

	DROP TABLE 삭제할 테이블 명

### 

##### (1) 테이블 삭제하기  
<img src="https://github.com/JSPlike/OpenSource/blob/gaeun/8.JPG?raw=true">


----------

### **3-3 DML **
#### 3-3-1 INSERT
INSERT는 테이블에 새로운 레코드를 삽입할 떄 사용하는 쿼리문이다.
명령어의 사용법은 다음과 같다.

	INSERT INTO 테이블명
	VALUES 레코드값

#### 

##### (1) 레코드 추가하기  
<img src="https://github.com/JSPlike/OpenSource/blob/gaeun/9.JPG?raw=true" >



----------
#### 3-3-2 DELETE
DELETE는 테이블에 조건에 맞는 레코드를 삭제할 때 사용하는 명령어이다.

	DELETE FROM 테이블명 [WHERE 삭제하려는 칼럼 명 = 값];



##### (1)  특정 레코드 삭제
SAL>2000의 조건을 만족한 레코드만 삭제  
<img src="https://github.com/JSPlike/OpenSource/blob/gaeun/11.JPG?raw=true" >

-----
##### (2) 모든 레코드 삭제  
<img src="https://github.com/JSPlike/OpenSource/blob/gaeun/12.JPG?raw=true">

----
##### (3) 그 외 삭제 명령

###### 1. TRUNCATE
테이블의 전체 데이터를 삭제하는 명령어이며 테이블에 외부키가 없다면 DELETE보다 훨씬 빠르게 삭제된다는 특징이 있다. 사용법은 다음과 같다.

	TRUNCATE 테이블명;

###### 2. DROP TABLE
테이블을 삭제하는 명령어이다. 위에서 한 번 소개한 적 있다. 사용법은 다음과 같다.

	DROP TABLE 테이블명;

----------

#### 3-3-3 Update
테이블에서 조건에 맞는 레코드의 내용을 변경할 때 사용하는 명령어이다.
사용법은 아래와 같다.

	UPDATE 테이블명 SET 수정할 레코드값 [WHERE 수정해야할 컬럼명 = 값]

----------

#### 3-3-4 Select
테이블에서 조건에 맞는 레코드를 검색할 때 사용하는 명령어이다.
사용법은 아래와 같다.

	SELECT 컬럼명 FROM 테이블명
	WHERE 조건
	GROUP BY 그룹화 컬럼(들)
	HAVING 그룹조건
	ORDER BY 컬럼명

----------

## **4. MySQL 사용중 오류발생**

### **4-1 버그 발생** 

MySQL은 버전별로 버그의 차이가 있다 이 문서에서 사용한 MySQL 버전은 5.7.20버전이다. MySQL을 사용하다보면 사용자의 잘못으로 생기는 버그 또는 시스템적으로 보유하고 있는 버그 등이 있다. <http://bugs.mysql.com> 를 통해서 MySql의 버그들을 확인할 수 있고 또 해결 할 수도 있다. 이 문서에는 MySQL을 사용하며 생길 수 있는 그리고 생겼던 몇가지 버그들을 다루어 볼 것이다.

## 
>**Note:**
>
이제 나올 몇가지 버그는 MySQL을 사용하면서 생겼던 버그 입니다. 버전에 따른 새로운 버그가 생길 수도 있으며 그러한 버그들에 대처하는 방법을 알고 있는 것이 중요합니다.
#### 

#### 4-1-1 **첫번째 버그 발생**

<img src="http://cfile27.uf.tistory.com/image/99BD9F335A28F96D2F720E">

처음 발생한 버그는 Node.js의 node-mysql 모듈을 사용하여 MySQL을 Connection하기위해 그 정보를 저장하고 MySQL과의 연동을 요청했을 때 에러가 발생했고 에러는 위의 메시지를 띄워주고 있다. 위의 에러메시지를 확대해서 보여주면 다음과 같다.

```
Host '127.0.0.1' is not allowed to connect to this MySQL server
```

루트 호스트인 127.0.0.1 또는 localhost에서 MySQL에 접속할 수 있는 연결을 허락하지 않는 다는 메시지 이며 이는 권한의 문제를 동반하고 있다. 처음 이 에러를 접했을 때 왜 루트 유저가 MySQL 서버에 접속할 수 없는지에 대한 의문이 있었지만 그건 MySQL 자체적인 문제인 걸로 따로 권한을 다시 설정해 주어야 한다.

이 문제를 해결하기 위해서는 먼저 새로운 MySQL을 접속할 유저를 생성해야 한다. 먼저 루트 권한으로 MySQL에 접속하자.
#### 
<img src="http://cfile1.uf.tistory.com/image/99B05E335A28FD4B0FF9F4">

>**Note:**
>
>권한이 있는 다른 유저로 접속해도 상관은 없지만 루트 유저로 접속하는 것이 낫다.

이제 MySQL 데이터 베이스 사용을 명시하기 위해 MySQL을 사용한다는 명령어인 **use mysql**을  입력해주고 새 유저를 만들어 보자

```
use mysql

CREATE USER 'joonyoung'@'localhost' IDENTIFIED BY '12341234';

CREATE USER '[새 유저이름]'@'localhost' IDENTIFIED BY '[새 비밀번호]';
```
#### 
<img src="http://cfile27.uf.tistory.com/image/9954EF335A28FE0B1DC118">

유저를 만들었다면 그 유저에 권한을 부여해 보자

```
GRANT ALL PRIVILEGES ON *.* TO 'joonyoung'@'localhost'

-> WITH GRANT OPTION;

GRANT ALL PRIVILEGES ON *.* TO '[유저 이름]'@'localhost'

-> WITH GRANT OPTION;
```
#### 
<img src="http://cfile8.uf.tistory.com/image/990DF2335A28FE8C25A7E9">

외부접속유저에게도 권한을 주기위해 같은 이름의 유저를 생성해 줍니다.
```
CREATE USER 'joonyoung'@'%' IDENTIFIED BY '12341234';

CREATE USER '[유저 이름]'@'%' IDENTIFIED BY '[유저 비밀번호]';
```
>**Note:**
>처음 유저생성 코드와의 차이점은 @뒤의 'localhost'와 '%'의 차이점 입니다. %는 local이 아님을 뜻할 수 있다.
#### 
<img src="http://cfile22.uf.tistory.com/image/997B89335A28FFBE124396">

그리고 나서 이 유저에 권한도 상향 설정 해줍니다.
```
GRANT ALL PRIVILEGES ON *.* TO 'joonyoung'@'%'

-> WITH GRANT OPTION;

GRANT ALL PRIVILEGES ON *.* TO '[유저 이름]'@'%'

-> WITH GRANT OPTION;
```
#### 
<img src="http://cfile26.uf.tistory.com/image/995729335A28FFCD1AB1FC">

여기까지 유저를 생성하고 새권한을 주는 과정을 진행해 보았다.

> 이 후에 이 유저를 통해 Connection을 진행하게 되면 처음 '127.0.0.1'에서 MySQL 허가를 받을 수 없다는 메시지는 뜨지 않는다.

# 


[^dbms]: [DBMS](https://en.wikipedia.org/wiki/Database/)는 다수의 사용자들이 데이터베이스 내의 데이터를 접근할 수 있도록 해주는 소프트웨어 도구의 집합이다.

[^mysql]: [MySQL](https://www.mysql.com/why-mysql/)은 현재 가장 많이 사용되고 있는 오픈소스형태의 관계형 데이터베이스 관리 시스템(RDBMS)이다.
