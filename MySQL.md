MySQL REFERENCE
===================


**DBMS와 MySQL 소개**
-------------
####DBMS
**데이터베이스 관리 시스템(DBMS)**[^dbms]은 다수의 사용자들이 데이터베이스 내의 데이터를 접근할 수 있도록 해주는 소프트웨어 도구의 집합입니다. DBMS은 사용자 또는 다른 프로그램의 요구를 처리하고 적절히 응답하여 데이터를 사용할 수 있도록 해줍니다.

DBMS는 크게 6가지의 기능을 가지고 있습니다.
>**Note:**

> - 정의 : 데이터에 대한 형식, 구조, 제약조건들을 명세하는 기능이다. 이때 데이터베이스에 대한 정의 및 설명은 카탈로그나 사전의 형태로 저장된다.
> - 구축 : DBMS가 관리하는 기억 장치에 데이터를 저장하는 기능이다.
> - 조작 : 특정한 데이터를 검색하기 위한 질의, 데이터베이스의 갱신, 보고서 생성 기능 등을 포함한다.
> - 공유 : 여러 사용자와 프로그램이 데이터베이스에 동시에 접근하도록 하는 기능이다.
> - 보호 : 하드웨어나 소프트웨어의 오동작 또는 권한이 없는 악의적인 접근으로부터 시스템을 보호한다.
> - 유지보수 : 시간이 지남에 따라 변화하는 요구사항을 반영할 수 있도록 하는 기능이다.

####MySQL
 **MySQL**[^mysql]은 DBMS중 관계형 데이터베이스 관리 시스템(RDBMS)에 분류되는 시스템입니다. MySQL은 페이스북, 구글, 어도비등 세계에서 가장 규모가 크고 빠르게 성장하는 기업들에서 사용되고 있는 관계형 데이터베이스 관리 시스템(RDBMS)입니다. 그러한 기업들은 이 시스템을 사용하여 대용량 웹 사이트, 비즈니스 크리티컬 시스템 및 패키지 소프트웨어에 전력을 공급하고 시간을 절약합니다.

MySQL은 표준 데이터베이스 질의언어인 SQL(Structured Query Language)를 사용하는 개방소스의 관계형 데이터베이스 관리 시스템이며, 속도가 빠르고 가볍고 유연하며, 초보자도 쉽게 다룰 수 있는 쉬운 인터페이스가 특징입니다.

또한, MySQL은 따로 데이터베이스를 관리하거나 자료를 관리하기 위한  GUI (Graphical User Interface)관리 툴이 내장되어 있지 않기 때문에 이용자들은 명령 줄 인터페이스도구를 이용하거나 또는 데이터베이스 또는 데이터베이스를 만들고, 관리하는데, 데이터를 백업하는데, 상태를 검사하고, 데이터베이스 구조를 생성하거는데, 또는 데이터 레코더를 작성하는데 있어서 MySQL 프론트엔드 데스크톱 소프트웨어나 웹 애플리케이션을 사용해야 한다.

####실습환경

>**환경:**

> - Ubuntu 16.04 LTS
> - MySQL
> - Apache 2.0
> - PHP 7.1
	 
	
 > **Tip:** 무작정 최신버전을 설치하는 것은 좋지 않습니다. 
	 

----------


**Documents**
-------------


### Tables

**Markdown Extra** has a special syntax for tables:

Item     | Value
-------- | ---
Computer | $1600
Phone    | $12
Pipe     | $1

You can specify column alignment with one or two colons:

| Item     | Value | Qty   |
| :------- | ----: | :---: |
| Computer | $1600 |  5    |
| Phone    | $12   |  12   |
| Pipe     | $1    |  234  |


```
// Foo
var bar = 0;
```

> **Tip:** To use **Prettify** instead of **Highlight.js**, just configure the **Markdown Extra** extension in the <i class="icon-cog"></i> **Settings** dialog.

> **Note:** You can find more information:

> - about **Prettify** syntax highlighting [here][5],
> - about **Highlight.js** syntax highlighting [here][6].


### Footnotes

You can create footnotes like this[^footnote].

  [^footnote]: Here is the *text* of the **footnote**.


### SmartyPants

SmartyPants converts ASCII punctuation characters into "smart" typographic punctuation HTML entities. For example:

|                  | ASCII                        | HTML              |
 ----------------- | ---------------------------- | ------------------
| Single backticks | `'Isn't this fun?'`            | 'Isn't this fun?' |
| Quotes           | `"Isn't this fun?"`            | "Isn't this fun?" |
| Dashes           | `-- is en-dash, --- is em-dash` | -- is en-dash, --- is em-dash |


### Table of contents

You can insert a table of contents using the marker `[TOC]`:

[TOC]


### UML diagrams

You can also render sequence diagrams like this:

```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```

And flow charts like this:

```flow
st=>start: Start
e=>end
op=>operation: My Operation
cond=>condition: Yes or No?

st->op->cond
cond(yes)->e
cond(no)->op
```

> **Note:** You can find more information:

> - about **Sequence diagrams** syntax [here][7],
> - about **Flow charts** syntax [here][8].


[^dbms]: [DBMS](https://en.wikipedia.org/wiki/Database/)는 다수의 사용자들이 데이터베이스 내의 데이터를 접근할 수 있도록 해주는 소프트웨어 도구의 집합이다.

[^mysql]: [MySQL](https://www.mysql.com/why-mysql/)은 세상에서 가장 많이 사용되는 오픈소스형태의 관계형 데이터베이스 관리 시스템(RDBMS)이다.


  [1]: http://math.stackexchange.com/
  [2]: http://daringfireball.net/projects/markdown/syntax "Markdown"
  [3]: https://github.com/jmcmanus/pagedown-extra "Pagedown Extra"
  [4]: http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference
  [5]: https://code.google.com/p/google-code-prettify/
  [6]: http://highlightjs.org/
  [7]: http://bramp.github.io/js-sequence-diagrams/
  [8]: http://adrai.github.io/flowchart.js/
