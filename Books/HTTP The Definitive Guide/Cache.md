캐시
==========
    웹 캐시는 자주 쓰이는 문서의 사본을 자동으로 보관하는 HTTP 장치다.
    웹 요청이 캐시에 도착했을 때, 사본이 존재한다면, 그 문서는 원 서버가 아니라 그 캐시로부터 제공된다.

불 필요한 데이터 전송
--------------
    복수의 클라이언트가 자주 쓰이는 원 서버에 페이지에 접근할 때,
    서버는 같은 문서를 클라이언트에게 각각 한 번씩 전송하게 된다.
> 캐시를 이용하면, 첫 번째 응답은 캐시에 보관되고 캐시된 사본이 뒤 이어 사용될 수 있기에 중복해서 트래픽을 주고받는 낭비가 줄어드게 된다.

대역폭 병목
--------------
    캐시는 또한 네트워크 병목을 줄여준다 많은 네트워크가 원격 서버보다
    로컬 네트워크 클라이언트에 더 넓은 대역폭을 제공한다.

요청 쇄도
-------
    캐싱은 갑작스런 요청 쇄도에 대처하기 위해 특히 중요하다.
    갑작스런 사건(뉴스 속보, 유명 인사와 관련된 사건)으로 인해 많은 사람이 접근할 때 이런 일이 발생한다.

거리로 인한 지연
------------
    비역 대역폭이 문제가 되지 않더라도, 거리가 문제가 될 수 있다.
    모든 네트워크 라우터는 제각각 인터넷 트래픽을 지연시킨다.

적중과 부적중
----------
    캐시는 유용하긴 하지만, 모든 문서의 사본을 저장하지는 않는다.
**캐시에 요청이 도착했을 때, 만약 그에 대응하는 사본이 있다면 그를 이용해 요청이 처리될 수 있다.**

> 이것을 캐시 적중이라고 부른다, 만약 사본이 없다면 원 서버로 전달되기만 할 뿐이다. *이것을 캐시 부적중이라고 부른다.*

재검사
----
    원 서버 콘텐츠는 변경될 수 있기 때문에, 캐시는 반드시 그들이 갖고 있는 사본이
    여전히 최신인지 서버를 통해 때떄로 점검해야 한다.

> 이러한 **신선도 검사를 '재검사'라고 부른다.**
캐시는 원한다면 스스로 사본을 재검사할 수 있지만, 수백만개씩 가지고 있는 경우가 흔한데 비해</br>
네트워크 대역폭은 부족하기 때문에, 대부분의 캐시는 클라이언트가 사본을 요청하였으며</br>
그 사본이 검사를 할 필요가 있을 정도로 충분히 오래된 경우에만 재 검사를 한다.

### 재검사 적중
사바 객체가 변경되었다면, 서버는 콘텐츠 전체와 함께 평범한 `HTTP 200 OK` 응답을 클라이언트에게 보낸다.
서버 객체가 변경되지 않았다면 `304 Not Modified` 응답을 보내고
> 신선도 검사를 해서 여전히 신선하다면 캐시 객체를 주고, 신선하지 않다면 서버 객체를 준다.

#### 갹체 삭제
    만약 서버 객체가 삭제되었다면, 서버는 `404 Not Found` 응답을 돌려보내며, 캐시 사본을 삭제한다.

### 적중률
    캐시가 요청을 처리하는 비율을 캐시 적중률, 혹은 문서 적중률이라고 부르기도 한다.
    적중률은 0에서 1까지의 값으로 되어 있지만, 흔히 퍼센트로도 표현되기 한다.
> 0%는 캐시 부적중, 그리고 100%는 모든 요청이 캐시 적중임을 의미한다.

### 바이트 적중률
    문서들이 모두 같은 크기인 것은 아니지만 문서 적중률이 모든 것을 말해주지는 않는다.
    몇몇 큰 객체는 덜 접근되지만 그 크기 때문에 전체 트래픽에는 더 크게 기여한다.
> 이런 이유는, 어떤 사람들은 바이트 단위 적중률 측정값을 더 선호한다.

바이트 적중률은 캐시를 통해 제공된 모든 바이트의 비율을 표현한다.
이 측정값은 트래픽이 절감된 정도를 포착해낸다.

> 문서 적중률과 바이트 단위 적중률은 둘 다 캐시 성능에 대한 유용한 지표다.

### 적중과 부적중의 구별
    불행이도, HTTP는 클라이언트에게 응답이 캐시 적중이었는지 아니면 원 서버 접근인지 말해줄 수 있는 방법을 제공하지 않는다.
    두 경우 모두 응답 코드는 응답이 본문을 갖고 있음을 의미하는 200 OK가 될 것이다.
    어떤 상용 프락시 캐시는 캐시에 무슨 일이 일어났는지 설명하기 위해 Via 헤더에 추가 정보를 붙인다.
> Date 헤더를 이용하여 캐시된 것을 알거나, Age 헤더를 이용하여 알 수 있다.

캐시 토폴로지
---------
캐시는 한 명의 사용자에게만 할당될 수도 있고 반대로 수천 명의 사용자들 간에 공유될 수도 있다.

> 개인 한 명에게만 할당된 캐시를 개인 전용 캐시라 부르고, 공유된 캐시는 공용 캐시라고 불러 사용자 집단에게 자주 쓰이는 페이지를 담는다.

### 개인 전용 캐시
    개인 전용 캐시는 많은 에너지나 저장 공간을 필요로 하지 않으므로, 작고 저렴할 수 있다.
    웹 브라우저를 통한 디스크, 메모리에 캐시해 놓고 설정 및 수정할 수 있도록 허용한다.
> 개인이 사용하기 때문에, 서버에 대하여 제각각 접근한다.

### 공용 프락시 캐시
    공용 캐시는 캐시 프락시 서버 혹은 더 흔히 프락시 캐시라고 불리는 특별한 종류의 공유된 프락시 서버다.
> 여러 사용자가 접근하기 때문에, 불 필요한 트래픽을 줄일 수 있는 더 많은 기회가 있다.

### 프락시 캐시 계층들
    작은 캐시에서 부적중이 발생했을 때, 더 큰 캐시가 그 '걸러 남겨진' 트래픽을 처리하도록 하는 계층을 만드는 방식이 합리적인 경우가 많다.
<img src="../Image/Accessing documents in a two-level cache hierarchy.png">

하지만, 캐시 계층이 깊다면 요청은 캐시의 긴 연쇄를 따라가게 될 것이다.</br>
**프락시 연쇄가 길어질수록 각 중간 프락시는 현저한 성능 저하가 발생할 것이다.**

### 캐시망, 콘텐츠 라우팅, 피어링
    몇몇 네트워크 아키텍처는 단순한 캐시 계층 대신 복잡한 캐시망을 만든다.
    캐시망의 프락시 캐시는 복잡한 방법으로 서로 대화하여, 어떤 부모 캐시와 대화할 것인지,
    아니면 요청이 캐시를 완전히 우회해서 원 서버로 바로 가도록 할 것인지 대한 결정을 동적으로 내린다.

캐시 처리 단계
-----------
### 단계 1: 요청 받기
    캐시는 네트워크 커넥션에서의 활동을 감지하고, 들어오는 데이터를 읽어드린다.
### 단계 2: 파싱
    캐시는 요청 메시지를 여러 부분으로 파싱하여 헤더 부분을 조작하기 쉬운 자료 구조에 담는다.
### 단계 3: 검색
    단계 3에서, 캐시는 URI를 알아내고 그에 해당하는 로컬 사본이 있는지 검사한다.

> 로컬 복사본은 메모리, 디스크나 다른 컴퓨터에 저장되있을 수도 있다.
**전문적인 수준의 캐시는 객체를 로컬 캐시에서 가져올 수 있는지 판단하기 위해 빠른 알고리즘을 사용한다.**

### 단계 4: 신선도 검사
    HTTP는 캐시가 일정 기간 동안 사본을 보유할 수 있도록 해준다.
    이 기간동안, 문서는 '신선'한 것으로 간주되고 캐시는 서버와의 접촉 없이 이 문서를 제공할 수 있다.
> 신선도 한계를 넘을 정도로 오래 갖고 있었다면 그 갹체는 '신선하지 않는' 것으로 간주되며,</br>캐시는 그 문서를 제공하기 전에 문서에 어떤 변경이 있었는지 검사하기 위해 서버와 재검사를 해야한다.

### 단계 5: 응답 생성
    캐시된 응답을 원 서버에서 온 것처럼 보이게 하고 싶기 때문에,
    캐시는 캐시된 서버 응답 헤더를 토대로 응답 헤더를 생성한다.

> 이 기저 헤더들은 캐시에 의해 수정되고 늘어난다.

**캐시는 클라이언트에 맞게 이 헤더를 조정해야 하는 책임이 있다.**

### 단계 6: 전송
    일단 응답 헤더가 준비되면, 캐시는 응답을 클라이언트에게 돌려준다.
    모든 프락시서버들과 마찬가지로, 프락시 캐시는 클라이언트와의 커넥션을 유지할 필요가 있다.
> 고 성능 캐시는 종종 로컬 저장장치와 네트워크 I/O 버퍼 사이에서 문서의 콘텐츠 복사를 피함으로써 데이터를 효과적으로 전송하기 위해 노력한다.

### 단계 7: 로깅
    대부분의 캐시는 로그 파일과 캐시 사용에 대한 통계를 유지한다.
    각 캐시 트랜잭션이 완료된 후, 캐시는 통계 캐시 적중과 부적중 횟수에 대한 통계를 갱신하고
    로그 파일에 요청 종류, URL 그리고 무엇이 일어났는지를 알려주는 항목을 추가한다.
- 페이지ㄹ 가까운 곳으로 거리지연

사본을 신선하게 유지하기
----------------------

    캐시된 사본 모두가 서버의 문서와 항상 일치하는 것은 이니다.
    결국 문서들은 시간에 따라 변경된다.

> HTTP는 어떤 캐시가 사본을 갖고 있는지 서버가 기억하지 않더라도, 사본이 서버와 충분히 일치하도록 유지할 수 있는 매커니즘인, 문서 만료와 서버 재검사라고 부른다.

### 문서 완료

    HTTP는 Cache-Control과 Expires라는 특별한 헤더들을 이용해서 원 서버가 각 문서에 유효기간을 붙일 수 있게 해준다.
    이 헤더들은 콘텐츠가 얼마나 오랫동안 신선한 상태로 보일 수 있는지 좌우한다.

> 캐시문서가 만료되기 전에, 캐시는 필요하다면 서버와 접촉 없이 사본을 제공할 수 있다.</br>그러나 일단 캐시가 만료되면, 캐시는 서버와 문서에 변경된 것이 있는지 검사해야 하며, 신선하지 않다면 사본을 얻어 와야 한다.

### 유효기간과 나이
    서버는 응답 본문과 함께 하는, HTTP/1.0+ Expires나 HTTPP/1.1 Cache-Control:max-age 응답 헤더를 이용해서 유효기간을 명시한다.
    Expires와 Cache-Control:max-age 헤더는 기본적으로 같은 일을 하지만, 절대 시간은 컴퓨터의 시계가 올바르게 맞추어져 있을 것을 요구한다.

### 서버 재검사

    캐시된 문서가 만료되었다는 것은, 그 문서가 원 서버에 현재 존재하는 것과 실제로 다르다는 것을 의미하지 않으며, 다만 이제 검사할 시간이 되었음을 뜻한다.
    이 검사를 캐시가 원 서버에게 문서가 변경되었는지의 여부를 물어볼 필요가 있음을 의미하는 '서버 재검사'라고 부른다.

- 재검사 결과 콘텐츠가 변경되었다면, 캐시는 그 문서의 새로운 사본을 가져와 오래된 데이터 대신 저장한 뒤 클라이언트에게도 도와준다.
- 재검사 결과 콘텐츠가 변경되지 않았다면, 캐시는 새 만료일을 포함한 새 헤더들만 가져와서 캐시 안의 헤더들을 갱신한다.

### 조건부 메서드와의 재검사
    HTTP의 조건부 메서드는 재검사를 효율적으로 만들어준다. HTTP는 캐시가 서버에게 '조건부 GET'이라는 요청을 보낼 수 있도록 해준다.
    이 요청은 서버가 갖고 있는 문서가 캐시가 갖고 있는 것과 다른 경우엔 객체 본문을 보내달라고 하는 것이다.

> 이런 식으로, 신선도 검사와 객체를 받아오는 것은 하나의 조건부 GET으로 결합된다.

**조건부 GET은 GET 요청 메시지에 특별한 조건부 헤더를 추가함으로써 시작된다.**

다섯가지 조건부 요청헤더를 정의하는데 그 중 둘은 캐시 재검사를 할 떄 가장 유용한 If-Modified-Since와 If-None-match이다.
> 모든 접근부 헤더는 'If-' 접두어로 시작한다.

- If-Modified-Since: \<tag>
    - 만약 문서가 주어진 날짜 이후로 수정되었다면 요청 메서드를 처리한다.
    - 이것은 캐시된 버전으로부터 콘텐츠가 변경된 경우에만 콘텐츠가 변경된 경우에만 콘텐츠를 가져오기 위해 Last-Modified 서버 응답 헤더와 함께 사용된다.

- If-None-Match: \<tag>
    - 마지막 변경된 날짜를 맞춰보는 대신, 서버는 문서에 대한 일련 번호와 같이 동작하는 특별한 태그를 제공할 수 있다.
    - If-None-Match 헤더는 캐시된 태그가 서버에 있는 문서의 태그와 다를 때만 요청을 처리한다.

#### If-Modified-Since: 날짜 재검사
    가장 흔히 쓰이는 캐시 재검사 헤더는 If-Modified-Since이다.
    If-Modified-Since 재검사 요청은 흔히 'IMS' 요청으로 불린다.

##### IMS 요청
    서버에게 리소스가 특정 날짜 이후로 변경된 경우에만 요청한 본문을 보내달라고 한다.

- 만약 문서가 주어진 날짜 이후에 변경되었다면, If-Modified-Since 조건은 참 -> 따라서 GET 요청은 평범하게 성공한다, 새 문서가 새로운 만료 날짜와 그 외 다른 정보들이 담긴 헤더들과 함께 캐시에게 반환된다.
- 변경되지 않았다면, 조건은 거짓이고, 서버는 작은 304 Not 응답 메시지를 클라이언트에게 돌려준다. 효율을 위해 본문은 보내지 않는다.

> If-Modified-Since 헤더는 서버 응답 헤더의 Last-Modified 헤더와 함께 동작한다.

원 서버는 제공하는 문서에 최근 변경 일시를 붙인다.
캐시가 캐시된 문서를 재검사 하려고 할 때, 캐시된 사본이 마지막으로 수정된 날짜가 담긴 If-Modified-Since 헤더를 포함한다.

> 만약 콘텐츠가 그동안 변경되었다면, 최근 변경 일시는 다를 것이다. 그리고 원 서버는 새 문서를 돌려줄 것이다.</br> **그렇지 않다면, 변경 일시와 같음을 발견하고 304 응답을 돌려줄 것이다.**

#### If-None-Match: 엔터티 태그 재검사

최근 변경 일시 재검사가 적절히 행해지기 어려운 상황이 몇가지 있다.

- 어떤 문서는 일정 시간 간격으로 다시 쓰여지지만 실제로는 같은 데이터가 포함되거나 내용에는 아무런 변화가 없더라도 변경시각은 바뀔 수 있다.
- 어떤 문서들의 변경은 전 세계의 캐시들이 그 데이터를 다시 읽어들이기엔 사소한 것일 수도 있다.
- 어떤 서버들은 그들은 갖고 있는 페이지에 대한 최근 변경 일시를 정확하게 판별할 수 있다.
- 1초보다 작은 간격으로 갱신되는 문서를 제공하는 서버들에게는, 변경일에 대한 1초의 정밀도는 충분하지 않을 수 있다.

    퍼블리셔가 문서를 변경했을 때, 그는 문서의 엔티티 태그를 새로운 버전으로 표현할 수 있다.
    엔티티 태그가 변경되었다면, 캐시는 새 문서의 사본을 얻기(GET)위해 If-None-Match 조건부 헤더를 사용할 수 있다.

캐시 제어
----------
    HTTP는 문서가 만료되기 전까지 얼마나 오랫동안 캐시될 수 있게 할 것인지 서버가 설정할 수 있는 여러 가지 방법을 정의한다.

### no-cache와 no-store 응답 헤더
    HTTP/1.1은 신선도를 관리하기 위해, 객체를 캐시하는 것을 제한하거나 캐시된 객체를 제공하는 여러 가지 방법을 제공한다.
    no-store와 no-cache 헤더는 캐시가 검증되지 않는 캐시된 객체로 응답하는 것을 막는다.

> 'no-store'가 표시된 응답은 캐시가 그 응답의 사본을 만드는 것을 금지한다.<br>캐시는 보통, 캐시가 아닌 프락시 서버가 그러는 것처럼, 클라이언트에게 no-store 응답을 전달하고 나면 객체를 삭제할 것이다.
> 'no-cache'로 표시된 응답은 사실 로컬 캐시 저장소에 저장될 수 있다.<br>**다만 먼저 서버와 재검사를 하지 않고서는 캐시에서 클라이언트로 제공될 수 없을 뿐이다.**

### Max-Age 응답 헤더
    Cache-Control: Max-age 헤더는 신선하다고 간주되었던 문서가 서버로부터 온 이후로 흐른 시간이고, 초로 나타낸다.
    또한 s-maxage 헤더는 max-age처럼 행동하지만 공유된(공용) 캐시에만 적용된다.

> 서버는 최대 나이먹음을 0으로 설정함으로써, 캐시가 매 접근마다 문서를 캐시하거나 리프레시하지 않도록 요청할 수 있다.

### Expires 응답 헤더
    더 이상 사용하지 않기를 권하는 Expires 헤더는 초 단위의 시간 대신 실제 만료 날짜를 명시한다.
    HTTP를 설계한 사람들은, 많은 서버가 동기화되어 있지 않거나 부정확한 시계를 갖고 있기 때문에, 만료를 절대시각 대신 경과된 시간으로 표현하는 것이 낫다고 판단했다.

> 신선도 수명의 근사값은 만료일과 생성일의 초 단위 시간차를 계산하여 얻을 수 있다.

### Must-Revalidate 응답 헤더
    캐시는 성능을 개선하기 위해 신선하지 않은 객체를 제공하도록 설정될 수 있다.
    만약 캐시가 만료 정보를 엄격하게 따르길 원한다면, 원 서버는 다음과 같은 Cache-Control을 붙일 수 있다.

> Cache-Control: must-revalidate 응답 헤더는 캐시가 이 객체의 신선하지 않은 사본을 원 서버와의 최초의 재검사 없이는 제공해서는 안 됨을 의미한다.
만약 캐시가 must-revalidate 신선도 검사를 시도했을 때 원 서버가 사용할 수 없는 상태라면, 캐시는 반드시 504 Gateway Timeout error를 반환해야한다.

### 휴리스틱 만료
    만약 응답이 Cache-Control: max-age 헤더나 Expires 헤더 중 어느 것도 포함하지 않고 있다면, 캐시는 경험적인 방법으로(휴리스틱) 최대 나이를 계산할 것이다.
    어떤 알고리즘이든 사용될 수 있지만, 계산 결과 얻은 최대 나이 값이 24시간보다 크다면, Heuristic Expiration 경고 헤더가 응답 헤더에 추가되어야 한다.
    우리가 알고 있는 바에 따르면, 이 경고 정보를 사용자가 볼 수 있게 해주는 브라우저는 거의 없다.

유명한 휴리스틱 만료 알고리즘의 하나인 LM 인자 알고리즘은, LM인자 알고리즘은, 문서가 최근 변경 일시를 포함하고 있다면 사용할 수 있다.
LM 인자 알고리즘은 최근 변경 일시를 문서가 얼마나 자주 바뀌는지에 대한 추정에 사용한다.

- 캐시된 문서가 마지막으로 변견된 것이 상당히 예전이라면, 급변할 가능성이 크지 않으므로, 캐시에 더 오래 보관하고 있어도 안전하다.
- 만약 캐시된 문서가 최근에 변경되었다면, 그것은 아마 자주 변경될 것이고, 따라서 우리는 그것을 서버와 재검사하기 전까지 짧은 기간 동안만 캐시해야 한다.

### 클라이언트 신선도 제약
    웹브라우저는 브라우저나 프락시 캐시의 신선하지 않은 콘텐츠를 강제로 갱신시켜주는
    리프레시나 리로드 버튼을 갖고 있다.

> 이 리프레시 버튼은 Cache-control 요청 헤더가 추가된 GET 요청을 발생시켜서,</br> 강제로 재검사하거나 서버로부터 컨텐츠를 무조건 가져온다.

**정확한 리프레시 동작은 각 브라우저나 문서, 중간 캐시 설정에 달려있다.**

클라이언트는 Cache-Control 요청 헤더를 사용하여 만료 제약을 엄격하게 하거나 느슨하게 할 수 있다.