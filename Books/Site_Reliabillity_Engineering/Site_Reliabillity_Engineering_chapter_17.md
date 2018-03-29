사이트 신뢰성 엔지니어링 Site_Reliabillity_Engineering<br>
챕터 17. 신뢰성을 위한 테스트
==========
## 테스트란?
    어떤 변경 사항이 일어났을 때 특정한 경우에서 동일한 결과를 기대할 수 있다는 매커니즘

>실제로 수행해야 하는 테스트의 양 = 신뢰성 요구 수준
<br>테스트로 인한 검증코드가 많아지면 불확실성과 변경에 의해 발생 가능한 잠재적인 신뢰성도 높아진다.

## 소프트웨어 테스트 종류
    소프트웨어 테스트는 크게 두 가지로 나누어진다.

- **전통적인 테스트**
    >SW가 올바른 동작을 수행 하는지
- **프로덕션 테스트**
    >WEB 서비스에 배포된 소프트웨어 시스템이 올바르게 동작 중인지 판단.
## 전통적인 테스트
### 단위테스트 (Unit Test)
    소프트웨어 특정 단위(함수, 클래스)로 테스트 하며 독립적으로 테스트를 진행함

### 통합 테스트
    단위 테스트를 통과한 소프트웨어 컴포넌트를 그보다 더 큰 규모의 컴포넌트에 편입된다.
    컴포넌트에 올바른 동작을 수행 하는지 검증하는 테스트가 통합테스트이다.

### 시스템 테스트
    배포 완료가 돼어있지 않은 시스템에 엔지니어가 수행 가능 한 큰 테스트

#### 스모크 테스트 (안전성 테스트)
    엔지니어가 시스템 내에 간단하지만 중요한 동작을 테스트 하는 방식이다.
    약간의 장애 상황을 가정한 테스트를 포함해 더 많은 부분을 테스트 한다.

#### 성능 테스트
    의존성을 가진 서비스의 응답 시간이나 시스템이 필요로 하는 자원에 대한 요구사항을 반드시 테스트 함
    시간이 지난 후 시스템의 성능이 줄거나 더 많은 자원을 사용하는지 확인 한다.

#### 회귀 테스트
    이미 알려진 버그를 통해 시스템의 실패 혹은 잘못된 결과가 나타는 것은 유추한다.

## 프로덕션 테스트
    실제 프로덕션 시스템을 대상으로 이루어지는 테스트이다.

#### 스트레스 테스트
    시스템과 시스템 컴포넌트들의 한계를 알 수 있는 테스트이다.

#### 카나리 테스트
    서버의 일부만을 새로운 버전의 바이너리나 설정 파일로 업그레이드 후 일정기간동안 살펴보는 형태
    만약에 문제 발생 x 점진적으로 업그레이드 한다.
    만약에 문제 발생 o 몇개의 서버만 원래대로 되돌린다.

### 테스트 및 빌드 환경
    현재의 테스트 커버리지가 낮거나 전무하다면 모든 핵심 기능과 클래스에 대해 단위 테스트를 하는 것은 벅차다.
    최소한의 노력으로 최상의 효과를 낼 수 있는 테스트를 하기 위해선 이와 같은 내용을 생각해야 함.
- 어떤 형태로든 기반 코드의 우선순위를 결정할 수 있는가?
    + 기능 개발과 프로젝트 관리 기법을 고려해 볼 때 모든 테스트가 높은 우선순위를 가지고 있다면 그 어떤 테스크도 우선순위가 높다고 할 수 없다.
    + 어떻게든 순서 결정이 가능한가?

- 정말로 사활이 걸려 있거나 비즈니스 관점에서 중요한 기능이나 클래스를 특정할 수 있는가?
    + 요금 청부는 보통 비즈니스 관점에서 중요한 업무다.

- 다른 팀들이 통합해서 사용하는 API 들이 있는가?
    + 지금까지 문제가 발생하지 않더라도 다른 개발팀이 이해하지 못한다면 API 대한 클라이언트를 잘못 작성하거나 혹은 최적의 상태로 구현하지 못할 수 있다.

>이렇게 적은 노력으로 큰 효과를 낼 수 있는 방법부터 시작하면 적정한 테스트를 거쳐 안정성을 확보한 소프트웨어를 출시할 수 있다.

```강력한 테스트 문화를 수집할 수 있는 방법 중 하나는 지금까지 보고된 모든 버그를 테스트 형태로 작성하는 것이다.```

## 결론
    테스트는 엔지니어들이 자신의 제품에 대한 신뢰성을 향상시킬 수 있는 적절한 투자수단이다.
    전체주기 동안 한두 번에 끝낼 수 있는 행위가 아니라 지속적인 행위다.