# android-payments

## Step4 구현 목록

- [x] Step3 피드백 반영
- [x] 카드 목록에서 카드 선택 리스너 추가
- [x] 카드 목록에서 카드 선택 시 카드 수정 화면으로 이동
    - [x] 카드 수정 화면 구현
    - [x] 카드 수정 화면에 기존 카드 정보 표시
- [] 카드 수정 시 변경사항이 있을 경우에만 수정

## Step4 진행 중 의식의 흐름

- 카드 수정 화면은 기존 카드 추가 화면인 NewCardScreen과 거의 동일하여 재사용해야만 할 것 같았습니다. 그래서 NewCardScreen을 수정하여 공통으로 사용하려고
  했습니다. 하지만 이렇게 하면 NewCardScreen의 기능이 더 복잡해지고 가독성이 떨어질 것 같아서 새로운 컴포넌트를 만들기로 결정했습니다.

## Step3 구현 목록

- [x] Step2 피드백 반영
- [x] 카드사 선택 화면 추가
- [x] 카드사 선택 시 카드 미리보기 이미지 변경

## Step3 진행 중 의식의 흐름

- 피드백을 반영하여 CardsScreen을 Stateful, Stateless로 나누어서 구현하니 프리뷰로 각각의 케이스를 정확히 표시할 수 있었습니다. 굿!
- expiredDate를 LocalDate로 변경하려고 했으나 만료일 초기 빈값을 주는 것이 어려워서 그냥 String으로 두었습니다. 여기 너무 매몰되어 더 중요한 부분을
  놓치고 있어서 입니다.
- ModalBottomSheet 구현 시 프리뷰에 아무 표시가 없어서 잘못된 코드인 줄 알고 한참을 고민했습니다. 프리뷰에서 보여주려면 어떻게 해야하나요? =>
  (자문자답) ModalBottomSheet의 컨텐츠 부분을 나눠서 Stateless 컴포넌트로 만드니까 프리뷰를 볼 수 있습니다!
- CardCompanies에 data라는 이름이 마음에 들지 않지만 적절한 네이밍이 생각나지 않습니다. 일단 이렇게...
- FlowRow에 사용되는 상수를 해당 컴포저블 바로 위에 선언하였습니다. 보통 최상위에 하는데 Tidy First에서 이렇게 가까이 두는 것도 언급해서 한번 해봤습니다.
- ModalBottomSheet를 hide한 후 CardsScreen으로 돌아왔을 때 터치 이벤트가 먹히지 않는 문제가 있습니다. 이 부분 해결이 쉽지 않네요. 하지만 해내겠죠?
- showBottomSheet의 상태를 확인하여 ModalBottomSheet를 hide 후 리컴포지션 발생 시 다시 컴포지션 되지 않도록 하여 터치 이벤트 문제를
  해결하였습니다.
- 여전히 의문인 점은 바깥 영역 터치로 Dismiss되는 것은 막아지지만 뒤로 가기 버튼으로는 상태 변경이 막아지지 않는다는 것입니다. 또한 onDismissRequest 호출
  시점에 대해 명확히 이해하지 못한 상태입니다.
- shouldDismissOnBackPress 속성으로 뒤로 가기 버튼을 막을 수 있었습니다. (feat. 강사님)
- 카드사 선택을 하면 카드사 이름과 카드 색상이 변경되어야 하고 등록된 카드 목록에도 해당 내용이 반영되어야 하는 과정이 복잡했습니다. 그래서 코드도 복잡해진 것 같습니다. 계속
  고민하기 보단 리뷰를 통해 개선하는 것이 좋을 것 같습니다.

## Step2 구현 목록

- [x] 카드 목록 화면 구현
    - [x] 상단바 추가
    - [x] 카드 등록 안내 문구 추가
    - [x] 카드 등록 이미지 추가
- [x] 새로운 카드 추가 시 카드 목록 업데이트
    - [X] 카드 데이터 저장소 추가
    - [x] 추가된 카드 목록에 표시
    - [x] 카드가 1개 이상 추가되면 안내 문구 숨김
- [x] 카드 목록에 카드가 2개 이상일 경우 카드 추가 상단바 표시
- [x] UI 변경사항 검증
- [x] 리팩터링

## Step2 진행 중 의식의 흐름

- onSaveButtonClicked에도 finish()를 호출하도록 해놓고 RESULT_OK를 수신하지 못한 것을 엉뚱한 부분만 보다가 시간을 많이 소비했습니다.
- 아직까지 컴포즈로 원하는 UI를 구현하는 것이 익숙하지 않아서 더 많은 시간이 연습이 필요할 것 같습니다. 카드 넘버의 숫자를 가로 여백없이 늘려서 표시하는 것이 어려웠습니다.
- 이전 미션까지는 테스트 코드를 작성해서 검증했습니다. 이번엔 Preview로 검증해 보려고 시도했습니다. CardScreen에 UI 상태에 따른 프리뷰를 추가하였습니다.
- 새로운 개념들이 등장하였고 시간을 쪼개서 하다보니 흐름이 끊겨서 오래 걸렸습니다. 더 미룰 수 없어서 마무리하였습니다.
