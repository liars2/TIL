어떻게 넷플릭스는 A/B 테스트를 하는지
==================
[*원본*](https://uxdesign.cc/how-netflix-does-a-b-testing-87df9f9bf57c)

당신은 평생동안 생각해본적이 있습니까? 왜 넷플릭스가 훌륭한 스트리밍 경험을 가지고 있는지에 대하여?
어떻게 그들이 완성된 홈페이지 뿐만 아니라 다른 UI 레이아웃들을 A/B 테스트를 통하여 재디자인하는 것을 당신이 배우기를 원합니까? 만약에 그렇다면, 그럼 이 아티클은 당신을 위한 것 입니다!
저는 시작할 것입니다 나의 요점을 공유함과 함께 디자이너와 괴짜들 이벤트로부터 나는 지난주 Yelp 에서 참여하였습니다. 그 두명의 굉장한 발표자 Anna Blaylock 과 Navin Iyengar, 넷플릭스에서의 두명의 제품 디자이너들은, 나왔던 넷플릭스의 10만명의 A/B 테스트에 대한 그들의 시간을 얻은것을 통한 이해, 그리고 그들의 디자인으로 부터의 생각을 도와주기 위한 제품의 몇 몇가지의 관련된 예제를 보여줍니다.

## 실험

저는 실험의 콘셉트를 설명할때 이 프레젠테이션의 첫번째 슬라이드를 매우 좋아했고 티비쇼인 Breaking Bad 이미지를 사용하는게 똑똑하다고 생각하였습니다 .

## 가설

과학에서, 가설은 생각 혹은 연구와 설명을 통하여 테스트 된 당신의 설명이다.
디자인에서, 이론과 추측은 가설이라고 부를 수 있다.

가설의 기본 아이디어는 어떤 결과를 미리 결정하는 것은 없다.
그것은 테스트 할 수 있고 그것들의 테스트가 모방될 수 있는 것이다.

> “A/B 테스트 뒤에 일반적인 콘셉트는 컨트롤 그룹과 개인 또는 다른 방법을 받는 것의 더 실험적인 그룹 (넷플릭스 안에서 “cells” 라고 불리우는)과 함께 경험을 만드는. 각각의 멤버들은 가만히 있는 것을 제외하고 경험을 주는 것과 함께 하나의 cells이, cells중 하나와 함께 항상 “기본 cells” 로 지정되어 있다. 이 cells은 컨트롤 그룹을 표현한다, 그 시험안에 모든 넷플릭스의 멤버는 시험안에 있지 않다는 같은 경험은 받는다.” - 넷플릭스 블로그

넷플릭스에서 A/B 테스트가 어떻게 끝나는지가 여기 있습니다:

 그 테스트가 시행되자마자, 그들은 중요성의 명확한 측정기준을 따라갑니다. 예를들어, 그것은 실시간 전송 시간과 보유한 것처럼 요소가 될 수 있습니다. 한번 그 참가자들은 충분히 의미있는 결론들로 부터 제공받는다, 그들은 각각의 테스트와 서로 다른 변화의 밖으로 승자가 정의되는 효험으로 움직입니다.

## 실험

실험하는 것의 행동은 실험 입니다. 넷플릭스 같은 많은 회사들이 유저 데이터를 변환하는 실험을 진행합니다. 가능한 효율적으로 관심있는 질문을 명확하게 이용가능하고 충분한 것의 데이터의 양과 두개의 종류가 반드시 적절한 실험을 준비하는데 노력하는 시간을 가져야 하는것은 물론 중요하다.
당신은 아마도 알아차렸을 것입니다 그 주요의 넷플릭스의 홈페이지가 보여주는게 바뀌는것처럼 보이는 것을 언제든 너가 로그인할때. 그들은 넷플릭스의 복잡한 경험의 모든 부분들 너에게 얻게 한다 그들에 쇼를 보게.
A/B 테스트의 아이디어는 보여준다 다른 컨텐츠를 다른 유저그룹에게, 그들의 리액션을 모으고 그 결과를 미래의 전략을 세우는데 사용한다. 넷플릭스의 엔제니어인 Gopal Krishnan 으로 부터 쓰여진 이 블로그 포스터에 따르면:

> 만약 당신이 멤버의 관심을 90초 안에 끌지 못한다면, 멤버는 관심을 잃을 가능성이 있고 또 다른 활동으로 넘어갈 것이다. 이런 실패된 세션들은 가끔식 될 수 있다 왜냐하면 우리가 옳은 컨텐츠를 보여주지 않았거나 또는 우리가 옳은 컨텐츠를 보여줬지만 왜 우리들의 멤버가 그것을 봐야하는지에 대한 충분한 증거를 제공받지 못했기 때문이다.

넷플릭스는 경험에 그들이 적은 아트워크를 타이틀에 대한 청중을 향상시키는 다양한 것을 만들수 있는지 아닌지 2013에 돌아가 보았습니다. 여기 그 결과입니다:

이것은 멤버들이 아트워크 변화에 대한 민감하다는 것의 이른 신호였습니다. 그것은 물론 그 신호에 넷플릭스의 경험 안 그들이 찾는 그 스토리의 종류를 넷플릭스 멤버들이 찾는것을 도와주는 가장 좋은 방법이 있다.
넷플릭스가 자동으로  다른 측면의 비율, 농작물, 수정들, 지역화 된 제목 처리 하지만 같은 뒷배경의 이미지를 가지고 있는 아트워크를 그룹짓는 시스템을 최근 만들었다.
그들은 그들의 다른 TV 쇼들을 추적한다 아트워크 퍼포먼스에 대한 경험을 모방된다.

이건 그 예입니다 :

이것들의 두 블로그 포스트들을 확인하여 넷플릭스의 A/B 테스트에 대하여 더 공부하세요 :
어떻게 넷플릭스는 A/B 테스트를 통한 비디오의 최고의 아트워크를 고르는가?
그 넷플릭스의 실험 플랫폼, 모든 넷플릭스 엔지니어팀이 가능하게 만드는 그 서비스는 전문적인 엔지니어 팀의 도움과 함께 그들의 A/B 테스트를 시행한다.

## 내가 배운 것

A/B 테스트는 유저의 행동을 배울때 가장 믿을 수 있는 방법. 디자이너에 대해서, 우리는 경험에 대한 렌즈를 통해 우리의 일에 대한 것이 생각 되어야 한다고.
1. 언제 그리고 왜 A/B 테스트인지.

제품의 디자인을 당신이 가지고 있을때, A/B 테스트를 사용하여 디자인과 타겟 두개의 키 매트릭스를 수정해라.: 보유와 수입. A/B 테스트에 의해 제품의 변화와 오랜 시간동안 유저를 추측하거나, 너는  너의 변화가 보유를 향상시키거나 혹은 수익을 향상시킬지 아닐지를 볼 수 있다. 만약 그렇다면, 기본으로 만들어라. 이 방법의 A/B 테스트는 사업 메트릭스에서 연달아 향상되곤 했다. 

2. 당신이 그들에게 원하는 것을 찾거나 혹은 하는것을 당신의 유저들은 찾거나 혹은 합니까?

나의 경험은 종종 여러번 유저들이 항상 그 일을 달성하지 못했다 너의 기대만큼 빨리, 그리고 가끔 그들은 심지어 너가 페이지에 넣은 확실한 버튼도 찾지를 못했다. 그 이유는 다양할 수 있다 : 그것이 아마 왜냐하면 그 디자인이 직감적으로 충분하지 않거나; 그 색깔이 생기가 충분하지 않거나; 그 유저가 기술에 능통하지 않거나; 그들은 모른다 어떻게 결정을 만들어야할지 왜냐하면 너무 많은 옵션들이 하나에 페이지에 있다, 기타 등등.

3. 당신의 직감이 맞습니까?

슬프게도, 유저의 행동이 올때, 우리의 직감들은 틀릴 수 있다, 그리고 유일한 방법은 A/B 테스트를 통하여 증명하는 것이다. 그것은 가장 좋은 방법이다 하나의 UX 디자이너가 다른 것보다 더 효과 있는지 아닌지 감정하는데. 일에서, 우리의 고객 제품 팀은 실제 재산 웹사이트에서 A/B 테스트를 통하여 증명되었습니다. 예를들어, 그들은 그들이 디자인 변화를 향상시키는 것이 google 광고를 누른 유저들에 대한 가입율을 만드는 것인지 아닌지 알아내길 원한다. 그들은 만들었다 몇몇의 다른 실험적 디자인과 그들을 테스트 하는 것을.
그들이 유일하게 숨긴 그 속성 이미지가 이긴다는 것에 그 디자인을 생각했지만, 두개의 속성 이미지와 높은 대화률을 가지고 있는 그 디자인을 찾았다.

4. 그 경계선들을 탐구하기

가장 최고의 아이디어들은 많은 아이디어 탐구들로 부터 온다. 일에서, 우리의 제품팀은 협력적으로 많은 다른 프로젝트들 사이로 일한다. 많은 파티들을 포함되고(개발자로 부터 제품 매니저 부터 디자이너 까지), 우리는 경계선들을 함께 탐구한다. 최고의 아이디어중 일부는 우리의 프로토 타입들중 테스트가 끝난 후 개발자 혹은 제품 매니저로 부터 나온다.
 
5. 사람들이 무엇을 하는지 감시하기, 그들이 말하는 것이 아닌.

유저들과 이야기 할때, 이것을 생각하는것은 중요하다: *그들은 항상 한가지만 말하지만 다르게 말한다.* 나는 이번주에 몇몇의 유저를 테스트 세션으로 안내했었다 그리고 하나의 완벽한 예제를 보여주었다.
 나는 이것을 하나의 유저에게 연락처 리스트를 보여주는 프로토 타입을 테스트 했고 그에게 물어봤었다 그가 평소에 그의 연락처를 정렬/필터 하는지 아닌지. 그는 아니라고 대답했다 왜냐하면 그는 필요하지 않았기 때문에. 어쨌든, 그가 새로운 필터들의 드롭다운 메뉴를 발견했을때, 그는 어떻게  편리하게 다수의 옵션을 한번에 정렬하고 걸러내는지에 의해 놀랐다 그리고 즉시 물어봤다 언제 제품으로 나오냐고.

6. 데이터를 사용해 기회의 크기를 추정하기
- 그것은 항상 이유들에 대한 것이다.
- 데이터는 형태 아이디어들을 도와준다.
- 어느 a/b 테스트가 충돌인지 아닌지 확인한다.

## Conclude

UI 와 UX 디자이너가 되는게 재미있지 않나요? 당신의 유저를 아는 것은 디자인 과정의 부분에서 가장 흥미있는것입니다! 어떤 디자인을 끝내는것 없습니다, 하지만 많은 반복인한 기회가 디자인을 향상시키고 최고의 경험의 가능성을 우리의 유저에게 줍니다!
나는 즐깁니다 그 기회를 만드는데 미묘한 수정을 우리의 유저들에게 그들의 리액션을 측정하고 그 제품 팀들과 함께 일하여 그 다음 스텝을 알아내기 원한다.
만약 이 아티클을 좋아하시면, 친절하게 하트 버튼을 눌러주세요!
