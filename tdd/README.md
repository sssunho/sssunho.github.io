# Test-Driven Development: By Example

시작한 날짜: 2020-01-12

`Clean code that works!` 작동하는 깔끔한 코드가 테스트 주도 개발의 궁극적 목표이다.



## 테스트 주도 개발의 규칙

- 오직 자동화된 테스트가 실패할 경우에만 새로운 코드를 작성한다.
- 중복을 제거한다.

> 테스트를 쉽게 만들려면 반드시 응집도는 높고 결합도는 낮은 컴포넌트들로 구성되게끔 설계해야 한다.



### 두 가지 규칙에 의한 프로그래밍 순서

1. 빨강
   실패하는 작은 테스트를 작성한다. 처음에는 컴파일조차 되지 않을 수 있다.
2. 초록
   빨리 테스트가 통과하게끔 만든다. 이를 위해 어떤 죄악을 저질러도 좋다.
3. 리팩토링
   일단 테스트를 통과하게만 하는 와중에 생겨난 모든 중복을 제거한다.

빨강/초록/리팩토링은 TDD의 주문과도 같은 것



#### 할일 목록 작성

앞으로 어떤 일을 해야 하는지 알려주고, 지금 하는 일에 집중할 수 있도록 도와주며, 언제 일이 다 끝나는지 알려줄 수 있게끔 할일 목록을 작성한다.

또다른 테스트가 생각날 수 있으며, 생각나면 할일 목록에 새로운 항목을 추가한다.

- 어떤 객체부터 있어야 할까?가 아닌 **우선 어떤 테스트가 필요할까?**의 관점으로 테스트 목록을 작성한다.



#### 테스트를 작성할 때

- 테스트 작성 순서는 작고 쉬워보이는 것부터 해라

  복잡해 보이는 것은 작은 단위로 나눠서 시작하던지, 아예 손을 대지 않는게 좋다.

- 가짜 구현에서 진짜 구현으로 작업하는게 명확할 때와 순방향으로 작업하는게 명확할 때가 있다.

  단순히 상수를 변수로 치환하는 일은 가짜에서 진짜 구현으로 작업하는 것

- 막대가 초록색이고 코드에 더 할 것이 명확하지 않으면 일단 그 상태에서 테스트를 작성한다.

- 클래스를 명시적으로 검사하는 코드가 있을 때에는 항상 다형성을 사용하도록 바꿔서 명시적인 클래스 검사를 제거한다.

- TDD로 구현할 땐 테스트 코드의 줄 수와 모델 코드의 줄 수가 거의 비슷한 상태로 끝난다.
- TDD가 자신의 방법에 비해 어떻게 다른지 직접 측정해 보아야 할 것이다. 이때 디버깅, 통합 작업, 다른 사람에게 설명하는 데 걸리는 시간 등의 요소를 반드시 포함해야 한다는 것을 기억하기 바란다.

- 미래에 코드를 읽을 다른 사람들을 염두에 둔 테스트를 작성한다.



### TDD 주기

1. 작은 테스트를 추가한다.
2. 모든 테스트를 실행하고, 실패하는 것을 확인한다.
3. 코드에 변화를 준다.
4. 모든 테스트를 실행하고, 성공하는 것을 확인한다.
5. 중복을 제거하기 위해 리팩토링한다.



## xUnit 

- 리팩토링의 일반적인 패턴 (TDD에서 볼 수 있는 리팩토링 패턴)

  하나의 특별한 사례에 대해서만 작동하는 코드를 가져다가 다른 여러 사례에 대해서도 작동할 수 있도록 **상수를 변수로 변화**시켜 일반화하는 것

  머릿속 순수한 추론에 의해 일반화하게 하지 않고, 잘 돌아가는 구체적인 사례에서 시작하여 일반화할 수 있게 해 준다. 

- **테스트를 작성하다보면 느끼는 3A 패턴**
  1. 준비(arrange): 객체를 생성한다.
  2. 행동(act): 어떤 자극을 준다.
  3. 확인(assert): 결과를 검사한다.

- 상위 클래스에 있는 속성만 사용하는 건 상위 클래스로 올라가는게 좋다.

- 테스트 커플링을 만들지 말 것
- 한번에 메서드 하나 이상 수정하지 않으면서 테스트가 통과하게 만들 수 있는 방법을 찾아내려고 노력해라
- 다른 테스트가 존재하고 잘 돌아간다면(그리고 오직 그럴 때에만) 테스트를 단순화할 수 있다

- 테스트를 구현하는 순서는 중요하다. 다음에 구현할 테스트를 선택할 때, 나에게 뭔가 가르침을 줄 수 있고 내가 만들 수 있다는 확신이 드는 것을 선택한다.
- 만약 테스트를 하나 성공시켰는데 그 다음 테스트를 만들며 문제가 생기면 난 **두 단계 뒤로 물러서는 것을 고려**한다.

- 실패한 테스트를 발견하면 좀더 세밀한 단위의 테스트를 작성해서 올바른 결과를 출력

- 중요한 문제를 발견했는데 이를 바로 처리하기보다는 할일 목록에 적어두었다

  > 한 테스트를 처리하다가 발견한 문제는 바로 처리하지 않고, 할일 목록에 추가해두고 풀고 있던 문제를 먼저 해결한다. (나중에 코드를 번복을 하게되더라도 괜찮다)

- TestSuite를 구현해야 하는 또 다른 장점은 컴포지트 패턴의 순수한 예제를 제공할 수 있다는 점이다.
- 아이템과 아이템의 모음(컴포지트)이 동일하게 작동할 수 있도록 run 메서드의 인터페이스를 변경

> **Composite pattern**
>
> 참고: https://mygumi.tistory.com/343
>
> - 객체 그룹을 조작하는 것처럼, 단일 객체를 조작할 수 있다.
> - 컴포지트의 의도는 트리 구조로 작성하여, 전체-부분 관계를 표현하는 것이다.



## 테스트 주도 개발의 패턴

테스트 한다는 것은 무엇을 뜻하는가? 테스트를 언제 해야 하는가? 테스트할 로직을 어떻게 고를 것인가? 테스트할 데이터를 어떻게 고를 것인가?



### 테스트 주도 개발 패턴

#### 테스트(명사)

- 작성한 소프트웨어를 어떻게 테스트할 것인가? 자동화된 테스트를 만들어라
- 프로그래밍 중 스트레스를 받기 시작할 때 **자동화된 테스트**를 실행한다. 테스트를 실행하여 초록 막대를 보면 좋은 느낌을 받게 되고 그러면 작업 중에 에러를 낼 일도 줄게 되며, 스트레스도 적어진다.



#### 격리된 테스트

테스트를 실행하는 것이 서로 아무 영향이 없어야 한다. 

- 테스트가 충분히 빨라서 직접, 자주 실행할 수 있게끔 만들자
- 테스트는 전체 애플리케이션을 대상으로 하는 것보다 좀더 작은 스케일로 하는 게 좋다
- 문제가 하나면 하나의 테스트만 실패해야 하고, 문제가 둘이면 두 개만 실패해야 한다
- 테스트가 실행 순서에 독립적이어야 한다. 테스트 일부만 실행해보고 싶으면, 선행 테스트가 실행되지 않아서 내가 고른 테스트들이 실패하지 않을까 걱정할 필요 없이 그렇게 할 수 있어야 한다.
- 테스트를 격리하기 위한 작업은 결과적으로 시스템이 응집도는 높고 결합도는 낮은 객체의 모음으로 구성되도록 한다.



#### 테스트 목록

- 시작하기 전에 작성해야 할 테스트 목록을 모두 적어둘 것

- 프로그래밍 스트레스를 줄이기 위한 우리 접근법의 첫 단계는 발 디딜 곳이 확실해지기 전엔 결코 발을 떼어 전진하지 말자는 것

- 모든 할일 목록을 컴퓨터 옆에 있는 종이 조각에 적어놓는 습관을 갖게 됐다. 비슷하게, 주 혹은 월 단위 목로도 만들어서 벽에 붙여뒀다.

  새로운 항목이 나타나면 나는 빠르고 의식적으로 이 항목이 '지금' 할일에 속하는지 '나중에' 할일에 속하는지, 또는 할 필요가 없는 일인지를 결정한다.

- 테스트를 통과하게 만드는 과정에서 여러분이 작성한 코드들은 새로운 테스트가 필요함을 암시적으로 알려줄 것이다. 이 새 테스트를 리팩토링과 마찬가지로 할일 목록에 적어 놓아라.

- 테스트가 주는 이익들(테스트는 프로그램 설계와 작업 범위 조절에 유용하다)은 스트레스가 어느 정도 존재할 때도 테스트를 작성하는 것이 좋음을 우리에게 알려준다.



#### 단언 우선

- 단언(assert)을 제일 먼저 쓰고 시작하라. 
  - 시스템을 개발할 때 무슨 일부터 하는가? 완료된 시스템이 어떨 거라고 알려주는 이야기부터 작성한다.
  - 특정 기능을 개발할 때 무슨 일부터 하는가? 기능이 완료되면 통과할 수 있는 테스트부터 작성한다.
  - 테스트를 개발할 때 무슨 일부터 하는가? 완료될 때 통과해야 할 단언부터 작성한다.
- 단언을 먼저 작성하면 작업을 단순하게 만드는 강력한 효과를 볼 수 있다. 구현에 대해 전혀 고려하지 않고 테스트만 작성할 때도 사실 여러분은 몇 가지 문제들을 한번에 해결하는 것이다.



### 빨간 막대 패턴

테스트를 언제 어디에 작성할 것인지, 테스트 작성을 언제 멈출지에 대한 것이다.



#### 한 단계 테스트

- 목록에서 다음 테스트를 고를 때 무엇을 기준으로 할 것인가?

  새로운 무언가를 가르쳐 줄 수 있으며, **구현할 수 있다는 확신이 드는 테스트를 고를 것**

- 아는 것에서 모르는 것으로 (known-to-unknown)

  우리는 아는 것에서 모르는 것으로 성장하는 프로그램을 갖게 된다.

#### 시작 테스트

- 오퍼레이션이 아무 일도 하지 않는 경우를 먼저 테스트할 것
- 현실적인 테스트 하나로 시작하면 너무 오랫동안 피드백이 없을 것이다. 
- 정말 발견하기 쉬운 입력과 출력을 사용하면 이 시간을 짧게 줄일 수 있다.

#### 설명 테스트

- 테스트를 통해 설명을 요청하고 테스트를 통해 설명하라. 그러면 자동화된 테스트가 더 널리 쓰이게 될 것이다.

#### 또 다른 테스트

- 어떻게 하면 주제에서 벗어나지 않고 기술적인 논의를 계속할 수 있을까?
- 주제와 무관한 아이디어가 떠오르면 이에 대한 테스트를 할일 목록에 적언호고 다시 주제로 돌아올 것
- 새 아이디어가 떠오르면 존중하고 맞이하되 그것이 내 주의를 흩뜨리지 않게 한다.
- 그 아이디어를 리스트에 적어놓고는 하던 일로 다시 돌아간다.

#### 회귀 테스트

- 시스템 장애가 보고될 때, 그 장애로 인하여 실패하는 테스트와 통과할 경우엔 장애가 수정되었다고 볼 수 있는 테스트를 가장 간단하게 작성하라
- 회귀 테스트를 작성할 때는 이 테스트를 작성해야 한다는 사실을 어떻게 하면 애초에 알 수 있었을지 생각해보라
- 애플리케이션 차원의 회귀 테스트는 시스템의 사용자들이 여러분에게 정확히 무엇을 기대했으며 무엇이 잘못되었는지 말할 기회를 준다.
- 시스템 장애를 해결하기 위해 리팩토링을 해야 한다면, 시스템이 여러분에게 다음과 같은 말을 한다는 뜻이다. "아직 내 설계를 마무리 못했구먼."

#### 휴식

- 피로는 판단력에 음성적인 영향을 끼치고, 판단력은 다시 피로에 음성적인 영향을 끼친다.
- 키보드로 뭘 쳐야 할지 알면, 명백한 구현을 한다. 잘 모르겠다면 가짜 구현을 한다.



### 테스팅 패턴

#### 자식 테스트

- 지나치게 큰 테스트 케이스를 어떻게 돌아가도록 할 수 있을까? 원래 테스트 케이스의 깨지는 부분에 해당하는 작은 테스트 케이스를 작성하고 그 작은 테스트 케이스가 실행되도록 하라. 그 후에 다시 원래의 큰 테스트 케이스를 추가하라
- 빨강/초록/리팩토링 리듬은 성공이 지속되는 데 너무나 중요하다
- 큰 테스트를 작성하고 나면 우선 교훈을 찾기 위해 노력해라. 왜 테스트가 그렇게 컸을까? 어떤 다른 방식을 취했더라면 좀더 작게 만들 수 있었을까? 지금 내 느낌은 어떤가?
- 거슬리는 테스트를 삭제하고 다시 시작할 수도 있다.
- 스스로 어떤 다른 방식으로 코딩하는지 관찰해 보고 적절한 방식을 선택하라

#### 모의 객체

- 비용이 많이 들거나 복잡한 리소스에 의존하는 객체를 테스트하려면 어떻게 해야 할까? 상수를 반환하게끔 만든 속임수 버전의 리소스를 만들면 된다.
- 해법의 대부분의 경우에 진짜 데이터베이스를 사용하지 않는 것이다. 
- 모의 객체는 당신이 모든 객체의 가시성(visibility)에 대해 고민하도록 격려해서, 설계에서 커플링이 감소하도록 한다.
- 모의 객체를 사용하면 프로젝트에 위험 요소가 하나 추가된다. 모의 객체가 진짜 객체와 동일하게 동작하지 않으면 어떻게 될까? 모의 객체용 테스트 집합을 진짜 객체가 사용 가능해질 때 그대로 적용해서 이러한 위험을 줄일 수 있다.

#### Self Shunt

> 참고: [SELF-SHUNT 패턴](https://ethdemor.wordpress.com/2010/10/06/self-shunt-패턴/)

- 한 객체가 다른 객체와 올바르게 대화하는지 테스트할 때, 테스트 대상이 되는 객체가 원래의 대화 상대가 아니라 테스트 케이스와 대화하도록 만든다.
- 별도의 객체를 만들지 않고, 테스트 케이스 자체를 사용한다. 즉 테스트 케이스가 일종의 모의 객체 노릇을 하는 것이다.
- 셀프 션트 패턴을 이용한 테스트가 그렇지 않은 테스트보다 읽기에 더 수월하다.
- 셀프 션트 패턴은 테스트 케이스가 구현할 인터페이스를 얻기 위해 인터페이스 추출(Extract Interface)을 해야 한다. 

#### 크래시 테스트 더미

- 호출되지 않을 것 같은 에러 코드(발생하기 힘든 에러 상황)를 어떻게 테스트할 것인가? 실제 작업을 수행하는 대신 그냥 예외를 발생시키기만 하는 특수한 객체를 만들어서 이를 호출한다.
- 테스트되지 않은 코드는 작동하는 것이 아니다. 이것이 안전한 가정 같다.
- 객체 전체를 흉내낼 필요가 없다는 점을 제외하면 크래시 테스트 더미는 모의 객체와 유사하다.

#### 깨진 테스트

**혼자서** 프로그래밍 할 때 프로그래밍 세션을 마지막 테스트가 깨진 상태로 끝마치는 것이 좋다.

#### 깨끗한 체크인

**팀** 프로그래밍을 할 때 프로그래밍 세션을 모든 테스트가 성공한 상태로 끝마치는 것이 좋다.