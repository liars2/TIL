마이크로서비스
============

마이크로 서비스란?
-------------
작고, 한가지 일을 하는데 주력하는 서비스. 이 것들은, 병합할 수 있으며 또 쉽게 쪼갤 수 있다.

마이크로 서비스가 나온 이유?
--------------------
> 모놀로식 코드베이스를 추구하더라도 중간 경계의 어딘가가 빈번히 무너지고, 버그를 고치거나 어려운 구현을 하는 과정에서</br>유사한 기능과 연관된 코드가 곳곳으로 퍼져나간다.

**크게 기획된 서비스를 지우려고 할 때, 많은 의존성으로 인해 빠르게 변하는 현대 개발 사회랑 맞지 않아서**

마이크로서비스, 마이크로?
------------------
마이크로라는 굉장히 작은 단위다. 이 단위의 서비스라고 생각했을 때 나는 처음 개미라고 생각했었다.
개미들은 따로 일하는 분야가 있다. 일 개미들은 일을 하고, 병정 개미는 외부와 전투 및 경호일을 하고, 여왕개미는 알을 낳는 일을 한다.

마찬가지로, 마이크로서비스는 단일 책임 원칙으로 **독립적인 일로 분류해,** 주어진 기능과 관련 코드들이 명확히 제자리에 있도록 하면서 서비스 경계를 비지니스 경계에 일치시킨다.

### 마이크로서비스의 크기?

    마이크로서비스의 크기는 어떻게 하나요? 더 작게 만들어야 하나요?

마이크로서비스의 크기는 충분히 작아서 더 이상 작아질 수 없는 크기로 만들면 된다.

이에 대한 확실한 대답을 하기 위해서는, 서비스가 팀 구조와 서로 얼마나 적절하게 배치되고 있는지 아는 게 중요하다.

### 자율성?
    마이크로 서비스는 작고 분리할 수 있는 개체다, 이것은 PaaS 상의 격리된 서비스이거나 운영체제 상의 프로세스가 될 수 있다.
    서비스 간의 분산도를 높히고, 서비스 간의 연결되어 생기는 문제점을 줄이기 위해서 모든 통신은 네트워크 통신으로 이루어 진다.

서비스들은 서로 독립적으로 변경될 수 있어야 하고, **소비자(서비스를 호출하는 다른서비스도 가능)를 변경할 필요 없이 독립적으로 배포되어야 한다.**

마이크로서비스의 주요 혜택
-----------------
### 기술 이기종성
    다수의 협업 서비스로 구성된 시스템에서는 각 서비스가 다른 기술을 사용하도록 결정할 수 있다.
**이는 결국 최소한의 공통점만을 지닌 표준화된, 만능의 접근 방식을 선택하기보다 각 작업에 적합한 도구를 선택하게 해준다.**

> 시스템 특정 부분의 성능을 높이려 할 때, 요구되는 성능 수준을 만족하는 데 유리한 다른 기술 스택을 고려해야 할 수도 있고 변환할 데이터를 어떻게 저장할지 결정해야 할 수도 있다.

예를들어, 포크와 숟가락이 필요하다고 포크 수푼을 만드는 것이 아닌 포크와 숫가락을 따로 만들면 되는 것이다.

**모놀로식 애플리케이션에서 새로운 프로그래밍 언어, 데이터베이스 또는 프레임워크를 시도하면 그 변경은 시스템에 큰 영향을 미치지만**

다양한 독립 서비스로 구성된 시스템에는 새로운 기술 분야를 시험해볼 만 한 곳이 많다.

### 회복성
    한 시스템의 컴포넌트에 장애가 발생하더라도 그 장애가 전파되지 않는다면 해당 문제를 격리하고
    나머지 시스템을 계속 작동시킬 수 있다.

감자에 싹이 텄다고 해서 감자를 못 먹는 것은 아니다.</br>
**감자에 싹 튼 부분을 도려내 먹으면 되다시피 분리(격리) 하면 된다!**

모놀리식 서비스에는 한 서비스가 고장나면 모든 것이 작동을 멈추지만
> 마이크로서비스에서는 서비스의 전체 장애를 차단하고 기능을 적절히 저하 시키는 시스템을 구축할 수 있다.

### 확장성
    하나의 큰 모놀리식 서비스에서는 항상 모든 것을 함께 확장해야 한다. 만약 전체 시스템에서 작은 한 부분만 성능이 떨어지는데,
    해당 동작이 거대한 모놀리식 애플리케이션에 묶여 있다면 전체를 한 덩어리처럼 확장해야 한다.

> 작은 서비스들로 구성되어 있다면 필요한 서비스만 확장할 수 있다.

### 배포 용의성
    백만 줄에 다하는 모놀리식 애플리케이션에서는 한 줄만 수정하더라도 해당 변경을 릴리즈 하기 위해
    전체 애플리케이션을 배포해야 하므로, 수차례의 릴리즈에 걸친 변경 사항이 한꺼번에 반영된다.

하지만, 마이크로서비스를 이용하면 하나의 서비스만 변경할 수 있고, 나머지 시스템과 독립적으로 배포할 수 있다.

**혹여나, 문제가 발생하더라도 롤백함으로써 해당 문제를 격리할 수 있다.**

### 조직 부합성
    대규모 팀에서는 코드베이스 때문에 생긴 문제가 많다
    더 작은 팀이 더 작은 코드베이슬 일할 때 더 생산적임을 우리는 알고 있다.

> 마이크로서비스를 이용하면 아키텍처를 조직 구조에 맞게 더 적절히 정렬할 수 있고,<br>최적의 팀 크기와 생산성을 위해 하나의 코드베이스에서 일하는 인원을 최소화할 수 있다.

### 조합성
    분산 시스템과 서비스 지향 아키텍처의 주요 장점 중 하나는 기능을 재사용할 기회가 많다는 것이다.
    마이크로서비스를 통해 다양한 방법과 목적으로 우리가 제공하는 기능이 소비되도록 할 수 있다.

> 웹사이트, 모바일 에플리케이션만 생각하는 시대는 끝났다! 각종 기기들(네이티브 앱, 웨어러블 장치 등등..) 연결할 방법을 고려해야 한다.

### 대체 가능성을 위한 최적화
    규모가 크다면, 몇 십년전에 볼 수 있는 시스템(포트란 등등..)을 볼 수 있을 것이다.
    교체 혹은 제거되지 않은 이유는 작업이 방대하고 수행하기도 어렵기 때문이다.

> 마이크로서비스는 더 나은 구현으로 교체하는 비용을 줄일 수 있으며, 심지어 삭제도 쉽게 할 수 있다.

서비스 지향 아키텍처란
-----------------
서비스 지향 아키텍쳐란 서비스의 최종 능력 집합을 제공하는 여러 서비스가 협업하도록 하는 설계 접근 방식이다.

    여기서 서비스란 일반적으로 완전히 분리된 운영시스템의 프로세스를 의미한다.
    서비스 간 통신은 네트워크 호출로 이루어진다.

기타 분해 기술
----------

### 공유 라이브러리
    거의 모든 언어가 지원하는 표준 부내 기술은 코드베이스를 여러 라이브러리로 나누는 것이다.
    이들 라이브러리는 서드파티에서 제공하거나 내부 조직에서 만들 수 있다.

라이브러리 팀과 서비스 간에 기능을 공유하도록 한다.
**이러한 라이브러리를 중심으로 팀이 구성될 수 있고 라이브러리를 재사용할 수도 있다.**

하지만 분명, 단점도 존재한다.

1. 진정한 기술 이기종성을 잃게 된다.
    - 일반적으로 라이브러리는 동일한 언어로 구현되거나 최소한 동일 플랫폼에서 실행되기 때문

2. 시스템 일부를 독립적으로 확장하기 어려워진다.

3. 동적 라이브러리를 사용하지 않는 한 전체 프로세스를 재배포하지 않고서는 새로운 라이브러리를 배포할 수 없으므로 변경 부분만 격리하여 배포할 수 있는 능력이 떨어진다.

4. 시스템 회복력을 보장하는 구조적 안전조치를 취할 명확한 접합부가 부족하다.

### 모듈

은총알은 없다
-----------
    마이크로서비스가 공짜도 망치도(모든것을 처리할 수 있는 도구), 복잡한 문제의 단순하고 신속한 해결책도 아니다.

마이크로서비스는 분산 시스템과 연관된 모든 종류의 **복잡성을 내포하고 있다.** 또한 시스템을 확대하고 회복력을 유지하는 방법에 대해 다르게 생각해야 할 것이다.