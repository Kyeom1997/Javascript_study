# 모던 자바스크립트 Deep Dive

최근 혼자서 리액트를 공부하면서 내가 이걸 과연 이해를 하면서 넘어가고 있는 건지, 아니면 그냥 코딩쇼를 보면서 따라치고만 있는 건지 회의감이 들기 시작했다. 분명히 혼자 HTML, CSS, Javascript를 할때는 어느 정도 이 코드들이 언제 사용되고 어떻게 사용되는 건지 알고치는 느낌이었다면 리액트는 그냥 온라인 강사분의 코드만 무지성으로 복사 붙여넣기 하는 기분이라서, 왜 그런지에 대해 생각해보았다. 결론은 자바스크립트 공부 부족. 자바스크립트를 확실히 알고 넘어가지도 못했으니 리액트를 이해하는 것은 아직 시기상조였던 것이다. 그래서 큰 맘 먹고 평소 동기가 추천했었던 모던 자바스크립트 Deep Dive를 구매하였다. 923쪽이라는 어마어마한 페이지 수가 나를 압도하였지만, 오늘부터라도 급하지 않게 천천히 내가 배운 것 만큼 정리하고 넘어가자는 취지로 TIL을 써보고자 한다.

<h2> 1장. 프로그래밍</h2>

<h3> 프로그래밍이란? </h3>
사람과 사람 사이에 의사소통을 하려면 커뮤니케이션이 필요하듯이, 프로그래밍은 사람이 컴퓨터에게 실행을 요구하느 일종의 <b>커뮤니케이션</b>이다. 다만 사람 사이의 의사소통과 다른 점은, 프로그래밍은 사람이 컴퓨터에게 해결해야 하는 문제(요구사항)를 <b>정확하고 상세하게 설명</b>하는 작업이라는 점이며, 그 결과물이 바로 코드다. 이때 필요한 것이 <b>Computational thinking(컴퓨팅 사고)</b>이다. 문제 해결 방안을 고려할 때 인간의 사고 방식에서 바라보는 것이 아닌, 컴퓨터의 입장에서 문제를 바라보는 것이다.

![](https://images.velog.io/images/hang_kem_0531/post/1591f859-0c53-4218-b178-c9159409d89e/%EB%AF%B8%EC%B9%9C%EB%86%88.gif)
~~컴퓨터가 말을 안듣는다고 때리면 안된다~~

예를 들어, "듣다"라는 행위는 사람에게 있어서 하나의 간단하고 당연한 기능으로 생각되지만, 컴퓨터에게는 이해하기 쉽지 않은 문제이다. 컴퓨터에게 "소리"의 개념에 대해 설명하려면, "소리 키워!" 같은 단순한 명령이 아닌 "볼륨을 1단계 크게 조정해줘", "볼륨을 60으로 조정해줘"와 같은 양적 개념인 숫자를 사용하여 명확하게 명령해야 한다는 것이다. 또한, "좋다", "붉다", "사랑"과 같은 관념적, 추상적 개념은 컴퓨터에게는 매우 난해한 개념이다.

![](https://images.velog.io/images/hang_kem_0531/post/b90b50a7-4f21-4339-b5d8-02ff2beb8ce1/image.png)

<h3>프로그래밍 언어</h3>
이렇게 문제 해결 능력을 바탕으로 정의된 문제 해결 방안은 컴퓨터에게 전달되어야 한다. 이때 명령을 수행할 주체는 컴퓨터이기 때문에, 사람은 컴퓨터가 이해할 수 있는 언어, 즉 기계어로 명령을 전달해야 한다. 하지만 사람이 기계어를 이해해서 기계어로 직접 명령을 전달하는 것은 우리가 사용하는 언어와 너무나도 체계가 다르기 때문에 매우 어려운 일이다.

그렇기 때문에 기계어로 직접 명령을 전달하는 것을 대신할 가장 유용한 대안으로 사람이 이해할 수 있는 약속된 구문(문법)으로 구성된 "프로그래밍 언어"를 사용하여 프로그램을 작성 후, 그것을 컴퓨터가 이해할 수 있는 기계어로 변환하는 일종의 번역기를 사용하는 방법이 채택되었다. 이 일종의 번역기를 **컴파일러** 혹은 **인터프리터**라고 한다. 프로그래밍 언어는 **구문(Syntax)**과 **의미(Semantics)**의 조합으로 표현된다.

<h3>구문과 의미</h3>
외국어를 잘하려면 외국어 화자의 말이나 문장을 정확히 이해한 후, 문맥에 따른 적절한 어휘 선택, 그리고 순차적으로 결론을 향해 나아가는 문장 구성이 필요하다. 즉, 문법에 맞는 문장을 구성하는 것은 물론 의미(Semantics)를 가지고 있어야 언어의 역할을 충실히 수행할 수 있다. 프로그래밍 언어도 마찬가지이다.

```js
const number = "string";
console.log(number * number); //NaN
```

자바스크립트의 변수에는 어떠한 타입의 값도 할당할 수 있기 때문에, 위 예제는 문법적으로는 전혀 문제가 없는 구문이다. 하지만 number라는 이름의 변수에 문자열이 할당되어 있기 때문에 의미적으로는 옳지 않다. 프로그래밍 언어는 문법에 부합하는 것은 물론이고, 수행하고자 하는 바를 정확히 수행하는 것, 즉 요구사항이 실현(문제가 해결)되어야 의미가 있다. 즉, 프로그래밍이란 **요구 사항의 집합을 분석해서 적절한 자료구조와 함수의 집합으로 변환한 후, 그 흐름을 제어하는 것**이라고 볼 수 있다.

---

<h2> 2장. 자바스크립트란? </h2>

<h3>자바스크립트의 탄생</h3>
1995년, 약 90%의 시장 점유율로 웹 브라우저 시장을 지배하고 있던 넷스케이프 커뮤니케이션즈는 웹 페이지의 보조적인 기능을 수행하기 위해 브라우저에서 동작하는 경량 프로그래밍 언어를 도입하기로 결정한다. 그래서 탄생한 것이 바로 브렌던 아이크가 개발한 자바스크립트이다.

이렇게 탄생한 자바스크립트는 현재 모든 브라우저의 표준 프로그래밍 언어로 자리 잡았다. 그러나 자바스크립트가 순탄하게 성장했던 것은 아니다. 자바스크립트가 탄생한 뒤 얼마 지나지 않아 자바스크립트의 파생 버전인 JScript가 출시되어 자바스크립트는 위기를 맞는다.

<h3>자바스크립트의 표준화</h3>
1996년 8월, 마이크로소프트가 자바스크립트의 파생 버전인 "JScript"를 인터넷 익스플로러 3.0에 탑재한 후, 넷스케이프와 마이크로소프트는 자사 브라우저의 시장 점유율을 높이기 위해 자사 브라우저에서만 동작하는 기능을 경쟁적으로 추가하기 시작했다. 이로 인해 브라우저에 따라 웹페이지가 정상적으로 동작하지 않는 <b>크로스 브라우징 이슈</b>가 발생하기 시작했고, 결과적으로 모든 브라우저에서 정상적으로 동작하는 웹페이지를 개발하기가 무척 어려워졌다.

이에 자바스크립트의 파편화를 방지하고 모든 브라우저에서 정상적으로 동작하는 표준화된 자바스크립트의 필요성이 대두되기 시작했고, 1996년 11월 넷스케이프는 ECMA 인터내셔널에 자바스크립트의 표준화를 요청, 상표권 문제로 자바스크립트는 **ECMASCript**로 명명되게 된다.

![](https://images.velog.io/images/hang_kem_0531/post/c0271aee-835b-4d9e-8eb6-633763a1594d/image.png)(출처:https://webroadcast.tistory.com/14)

<h3>자바스크립트 성장의 역사</h3>
초창기 자바스크립트는 웹페이지의 보조적인 기능을 수행하기 위해 한정적인 용도로 사용되었다. 이 시기에 대부분의 로직은 주로 웹 서버에서 실행되었고, 브라우저는 서버로부터 전달받은 HTML과 CSS를 단순히 렌더링 하는 수준이었다.

> **렌더링(rendering)**
> 렌더링이란 HTML, CSS, 자바스크립트로 작성된 문서를 해석해서 브라우저에 시각적으로 출력하는 것을 말한다. 때로는 서버에서 데이터를 HTML로 변환해서 브라우저에게 전달하는 과정(SSR; Server Side Rendering)을 가리키기도 한다.

<h4> Ajax </h4>

1991년, 자바스크립트를 이용해 서버와 브라우저가 <b>비동기</b> 방식으로 데이터를 교환할 수 있는 통신 기능인 **Ajax**가 **XMLHttpRequest**라는 이름으로 등장했다.

이전의 웹페이지는 완전한 HTML 코드를 서버로부터 전송받아 웹페이지 전체를 렌더링하는 방식으로 동작했기 때문에, 화면이 전환되면 웹페이지 전체를 처음부터 다시 렌더링해 순간적으로 깜빡이는 현상이 발생하고, 성능 면에서도 불리했다. 하지만 Ajax의 등장은 이전의 패러다임을 획기적으로 전환했다. 즉, 웹페이지에서 변경할 필요가 없는 부분은 다시 렌더링하지 않고, 서버로부터 필요한 데이터만 전송받아 변경해야 하는 부분만 한정적으로 렌더링하는 방식이 가능해진 것이다. 이로써 웹 브라우저에서도 데스크톱 애플리케이션과 유사한 빠른 성능과 부드러운 화면 전환이 가능해졌다.

<h4> Node.js </h4>

2009년, 라이언 달이 발표한 Node.js는 구글 V8 자바스크립트 엔진으로 빌드된 자바스크립트 런타임 환경으로, **브라우저의 자바스크립트 엔진에서만 동작하던 자바스크립트를 브라우저 이외의 환경에서도 동작**할 수 있도록 자바스크립트 엔진을 브라우저에서 독립시킨 자바스크립트 실행 환경이다. Node.js는 다양한 플랫폼에 적용할 수 있지만 서버 사이드 애플리케이션 개발에 주로 사용되며, 이에 필요한 모듈, 파일 시스템, HTTP 등 빌트인(내장) API를 제공한다.

Node.js는 자바스크립트 엔진을 기반으로 하므로 이 환경에서 동작하는 애플리케이션은 자바스크립트를 사용하여 개발하는데, FE와 BE 영역에서 자바스크립트를 사용할 수 있다는 동형성은 별도의 언어를 학습하기 위한 시간을 덜 수 있다는 장점이 있다. 또한 Node.js는 **비동기 I/O**를 지원하며 **단일 스레드 이벤트 루프 기반**으로 동작함으로써 요청 처리 성능이 좋다.

<h4> SPA 프레임워크 </h4>

모던 웹 애플리케이션은 데스크톱 애플리케이션과 비교해도 손색없는 성능과 사용자 경험을 제공하는 것이 필수가 되었고, 더불어 개발 규모와 복잡도도 상승했다. 이러한 필요에 따라 많은 패턴과 라이브러리가 출현했고, 개발에 많은 도움을 주었지만 변경에 유연하면서 확장하기 쉬운 애플리케이션 아키텍처의 구축이 어려워 졌기 때문에, 필연적으로 프레임워크가 등장하게 되었다.

이러한 요구에 발맞춰 CBD 방법론을 기반으로 하는 SPA(Single Page Application)가 대중화되면서 Angular, React, Vue.js, Svelte 등 다양한 SPA 프레임워크/라이브러리 또한 많은 사용층을 확보하고 있다.

<h3> 자바스크립트의 특징 </h3>

자바스크립트는 HTML, CSS와 함께 웹을 구성하는 요소 중 하나로 **웹 브라우저에서 동작하는 유일한 프로그래밍 언어**이며, 개발자가 별도의 컴파일 작업을 수행하지 않는 **인터프리터 언어**이다. 인터프리터는 소스코드를 즉시 실행하고 컴파일러는 빠르게 동작하는 머신 코드를 생성하고 최적화 한다. 대부분의 모던 자바스크립트 엔진(크롬의 V8, 사파리의 JavaScriptCore 등등)은 인터프리터와 컴파일러의 장점을 결합해 비교적 처리 속도가 느린 인터프리터의 단점을 해결했다.

자바스크립트는 명령형, 함수형, 프로토타입 기반 객체 지향 프로그래밍을 지원하는 **멀티 패러다임 프로그래밍 언어**다.

---
