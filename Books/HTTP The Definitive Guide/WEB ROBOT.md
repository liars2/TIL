웹 로봇
===================
    사람과의 상호작용 없이 연속된 웹 트랜잭션들을 자동으로 수행하는 소프트웨어 프로그램이다.
> 웹 사이트에서 다른 웹 사이트로 떠돌아다니며, 콘텐츠를 가져오고 하이퍼링크를 따라가고, 발견한 데이터를 처리함.

**'크롤러', '스파이더', '웜', '봇' 등으로 각양각색의 이름으로 불린다.**

만들어진 계기
------------------------
    웹 로봇의 사용 용도를 예를 들면 다음과 같다.
- 주식시장 서버에 GET 요청을 보내, 받은 응답으로 주가 추이 그래프를 생성하는 그래프 로봇
- WWW 규모와 진화에 대한 통계 정보를 수집하는 웹 통계 조사 로봇
    > 페이지 개수, 크기, 언어, 미디어 타입등을 기록
- 검색 DB를 만들기 위해 모든 문서를 수집하는 로봇
- 상품에 대한 가격 DB를 만들기 위해 온라인 쇼핑몰의 카탈로그에서 웹페이지를 수집하는 가격 비교 로봇

크롤러와 크롤링
------------------------
    웹 크롤러는, 먼저 웹페이지를 한 개 가져오고 그 다음 그 페이지가 가르키는 모든 페이지를 가져오고
    다시 그 페이지를 가져오는 재귀적으로 반복하여 웹을 순회한다.

> 이런 크롤러들은 이런 방식으로 돌아다닌다.

### 어디에서 시작하는가: 루트 집합
<img src="../Image/root_set.png">
크롤러가 방문을 시작하는 URL들의 초기 집합은 루트 집합이라고 부른다.
루트 집합을 고를 때, 충분히 다른 장소에서 URL들을 선택해야 한다.

만약 위 그림의 웹을 크롤링을 한다면 실제처럼 모든 문서로 이어지게 되는 하나의 문서란 없다.

### 링크 추출과 상대 링크 정상화
크롤러가 크롤링을 진행하면서 탐색해야 할 새 링크를 발견함에 따라, 이 목록은 급속히 확장됨.

### 순한 피하기
<img src="../Image/WEB_LOOP.png">
이와 같은 사태를 방지하기 위해서는 로봇들이 어디를 방문했는지 알아야 한다.
순환은 로봇을 함정에 빠뜨려서 멈추게 하거나 진행을 느려지게 한다.

로봇에 필요한 요소들
------------------------
    로봇은 다른 HTTP 클라이언트 프로그램과 다르지 않다.
    HTTP 요청을 만들고, 적절한 요청 헤더를 사용해야한다.

**로봇 구현자들은 로봇의 능력, 신원, 출신을 알려주는 기본적인 몇 가지 헤더를 사이트에게 보내주는 것이 좋다.**

User-Agent<br>
    **서버에게 요청을 만든 로봇의 이름을 말해준다.**
From<br>
    **로봇의 사용자/관리자의 이메일 주소를 제공한다.**
Accept<br>
    **서버에게 어떤 미디어 타입을 보내도 되는지 말해준다.**
Referer<br>
    **현재의 요청 URL을 포함한 문서의 URL을 제공한다.**

이는 잘못된 크롤러의 소유자를 찾아낼 때와 서버에게 로봇이 어떤 종류의 콘텐츠를 다룰 수 있는지에 대한 약간의 정보를 주려 할 때 모두 유용한 정보다.

나쁜 로봇들
------------------------
    제멋대로인 로봇들이 아수라장을 만들 여러 가능성이 있다.
    로봇들이 저지르는 실수와 그로 인해 초래되는 결과는 다음과 같다.

### 폭주하는 로봇
    사람보다 많고 빠른 HTTP 요청을 줄 수 있어 만약 로봇이 논리적인 에러, 순환에 빠진다면
    극심한 부하를 일으켜 서버에 과부화를 유발해서 서비스 장애를 일으킬 수 있다.

### 오래된 URL
    만약 웹사이트가 그들의 콘텐츠를 많이 바뀌어, 존재하지 않는 URL에 요청한다면
    서버의 에러로그로 가득 채워지거나, 에러 페이지를 제공하는 부하로 인해 장애를 일으킬 수 있다.

### 호기심이 지나친 로봇
    어떤 로봇들은 사적인 URL을 얻어 그 데이터를 인터넷 검색엔진이나
    기타 애플리케이션을 통해 쉽게 접근할 수 있도록 만들 수도 있다.

> 그 웹페이지를 적극적으로 알리는 것을 원치 않았다면, 사생활 침해라고 여길 것이다.

### 동적 게이트웨이 차단하기
    로봇들이 그들이 접근하고 있는 것에 대해 언제나 잘 알고 있는 것은 아니다.
    원치않게 게이트웨이 URL로 요청한다면, 특수 목적 처리 비용이 많이 들 것이다.


Robots.txt
------------------------
### 로봇 차단하기.
    이런 로봇들을 단순히 차단 혹은 원하는 콘텐츠만 보여줄 수 있게 협약한 것이
    Robots.txt 다.

#### 모든 로봇 차단하기
```text
User-agent: *
Disallow: /
```
이런식으로, 로봇들을 차단할 수 있다.
http://www.naver.com/robots.txt
> 네이버의 robots.txt 파일