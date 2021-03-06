Intro.JS

해당 저장소는 <a src="https://introjs.com/docs/">introjs</a> 공식 홈페이지 를 참고하여 만들어졌음을 밝힙니다.

IntroJs 는 각 단계에서 원하는 부분에 포커스를 주어 사용자의 시선을 집중시키기 위해 개발된 라이브러리 입니다.

## 설치

CDN

```HTML
<script src="https://cdnjs.cloudflare.com/ajax/libs/intro.js/3.2.1/intro.js"></script>\
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/intro.js/3.2.1/introjs-rtl.css" integrity="sha512-3eskNfJHA0L8y9EWaHqgxCJ+A3geYz7sWgr9YZ9Tp7oFtquhPbeM+TawucTX8Ze8/Z67rwTEbUe1EzoOE3SnyA==" crossorigin="anonymous" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/intro.js/3.2.1/introjs.css" integrity="sha512-i+WzzATeaDcwcfi5CfLn63qBxrKqiQvDLC+IChU1zVlaPguPgJlddOR07nU28XOoIOno9WPmJ+3ccUInpmHxBg==" crossorigin="anonymous" />
```

NPM

```javascript
npm install intro.js --save
```

Git 을 통해서도 사용이 가능하나 업데이트가 늦어지는 편, 권장하지 않는다.

## data-intro

IntroJS 의 가장 기초적인 명령어는 data-intro 이다.
말 그대로 도움말의 제목을 정의하는 것 인데,

```html
<a href='http://example.com/' data-intro="Hello World! I'm Intro.js">Intro.js</a>
```

를 입력하고 

```javascript
introJs().start();
```

의 결과는 아래와 같다

<img src="gitImages\data-intro.png">

## data-title

data-title 이란 해당 하이라이트 박스의 제목 부분으로써,

```html
<a data-title="!Welcome" data-intro="!Hello World 👋"></a>
```

위와 같이 적어준다면 아래와 같은 결과를 볼 수 있다.

<img src="gitImages\title&intro.png">

## 상업용 라이선스

intro.js 의 경우 상업적으로 이용할 경우 적절한 라이선스 구매를 권장하고 있다.

<img src="gitImages\license.png">

상업용 라이선스 구매 시 공식적인 지원이 되는데

1. intro.js 설정 도움

2. intro.js 사용자 정의 가능

3. 라이브러리 관련 질문 즉답

## JSON 지원

intro.js 는 html 에서 각 태그에 data-(something) 을 설정하지 않더라도
JSON 형식으로 전달하여 실행 또한 가능하다

```javascript
introJs().setOptions({
    steps: [
        // 첫 번째 하이라이트
        {
            // element 를 정의하지 않았으므로 화면의 중앙 에 포커스가 잡힘
            title: 'Welcome',
            intro: 'Hello World! 👋'
        },
        // 두 번째
        {
            // title 을 정의하지 않았으므로 제목 생략
            element: document.querySelector('.card-demo'),
            intro: 'This step focuses on an image'
        },
        // 세 번째
        {
            // card__image 라는 className 을 가진 요소에게 포커스가 잡힘
            title: 'Farewell!',
            element: document.querySelector('.card__image'),
            intro: 'And this is our final step!'
        }
    ]
}).start();
```

여기까지만 보면 오히려 외워야 할 구문도 많고 굳이 왜 써야하나 싶겠지만


```javascript
intro: '<img src="https://i.giphy.com/media/ujUdrdpX7Ok5W/giphy.webp" onerror="this.onerror=null;this.src=\'https://i.giphy.com/ujUdrdpX7Ok5W.gif\';" alt="">'
```

만약 HTML 태그를 강조하는 것이 아닌 강조 메시지 안에 태그를 담아내고 싶다면 JSON 형식의 intro 를 사용하여야 한다.

<img src="gitImages\magic.png">

## intro position

HTML 태그가 화면의 가장 왼쪽에 붙어있다면, 당연하게 인트로는 오른쪽, 상단, 하단 중 위치되어야 할 것이다. JSON 형식의 Intro.js를 사용하면 이를 제어할 수 있다.

```javascript
introJs().setOptions({
  steps: [
    {
        element: document.querySelector('.card-demo'),
        intro: 'Tooltip has position right',
        position: 'right'
    },
    {
        element: document.querySelector('.card-demo-link'),
        intro: 'Tooltip has position left',
        position: 'left'
    },
    {
        element: document.querySelector('.card-demo-text'),
        intro: 'Tooltip has position bottom',
        position: 'bottom'
    },
    {
        element: document.querySelector('.card-demo'),
        intro: 'Tooltip has position top',
        position: 'top'
    }
]
}).start();
```

position key 의 value 로 방향을 지정하면 해당하는 방향에 intro 가 생기게 된다.

## hint

intro.js의 주목해야 할 두 번째 속성은 hint 이다.

```html
<small data-hint="You can select the text" data-hintposition="top-right">
    The Quaco Head Lighthouse is a well maintained lighthouse close to St.
    Martins. It is a short, beautiful walk to the lighthouse along the
    seashore.
</small>
```

위 구문에서 유심히 봐야 할 점은 data-hint 속성의 문자열이 아래 사진과 같이 표기되는 것이며 이 또한 data-hintposition 으로 관리가 가능하다.

<img src="gitImages\hint.png">

## CSS

Intro.JS의 스타일링은 매우 간단하다.

```javascript
introJs().setOptions({
  tooltipClass: 'testStyle'
}).start()
```

을 적용한다면

```css
.testStyle {
    color:hotpink;
}
```

아래와 같은 스타일이 적용된다.

## ProgressBar

상태 진행바를 표기하는 방법은 매우 간단하다 JSON 형식의 데이터객체에 옵션을 true 로 설정해주면 되는데

```javascript
introJs().setOptions({
    // 상태표시줄 표시
    showProgress:true
}).start();
```

<img src="gitImages\progress_bar.png">

## hideButton

다음 혹은 이전 intro 를 대상으로 이동할 수 없도록 버튼을 가릴 수 있는데

```javascript
introJs().setOptions({
    // intro 의 모든 버튼을 가림
    showButtons:false,
}).start();
```

해당 옵션에 Boolean 값을 부여함에 따라 보이게 할 수도 보이지 않게 할 수도 있다.

<img src="gitImages\hideButton.png">

## showBullets

여러 flag 를 보지않고 깔끔한 텍스트와 이동 버튼만 보이게 하고 싶다면 
JSON 형식의 데이터에서

```javascript
introJs().setOptions({
    // flag 들을 모두 제거
    showBullets:false,
}).start();
```

위와 같이 showBullets 의 값을 false 로 주면된다.

<img src="gitImages\hideBullets.png">

## disableInteraction

사용자로 하여금 intro 진행 도중 다른 링크 혹은 버튼이 클릭됨을 방지하려면

```javascript
introJs().setOptions({
    // 클릭방지
    disableInteraction:true,
}).start();
```

이제 해당 링크 혹은 텍스트 모든 부분에 클릭이 불가능해진다.

## Right to Left

RTL 이란 한글 혹은 영문 등 대부분의 왼쪽에서 오른쪽으로 읽는 문자와 다르게
بعد 등 오른쪽에서 왼쪽으로 읽어가는 언어를 말한다.

introjs 는 이 점을 고려하여 بعد 와 같은 언어를 사용하면 별도의 설정 없이도 텍스트가 오른쪽에 붙어 출력된다.

<img src="gitImages\RTL.png">

## onBeforeExit

introJS 의 on 이벤트는 대표적으로 한 가지가 있는데, 바로 상호작용을 종료시키기 전 의사를 물어보는 onBeforeExit 이다. 사용자가 예 를 눌러 true 를 반환한다면 종료되고, 반대의 경우 종료되지않고 그대로 진행된다.

```javascript
introJs().onbeforeexit(function () {
    // 모든 이벤트는 종료 전 물어보는 것이 좋다.
  return confirm("Are you sure?");
}).start()
```

<img src="gitImages\onBeforeExit.png">

## Advanced

data-intro 속성을 가진 HTML 태그라면 introJs().start() 를 할 경우 포커싱이 잡힘

스크롤이 가능한 위치에 있다면 포커싱이 잡힘

```javascript
introJs().start()
```

## Step

introJS 는 Step이라 하는 여러 단계로 분류되는데

```javascript
introJs().goToStep(2).start();
```

를 호출한다면 2번 단계부터 소개를 시작한다.
해당 단계를 정의하는 방법은 HTML 기준으로

```html
<!-- 아래와 같다면 goToStep(3) -->
<div id="third" data-step='3'></div>
```

위와 같이 설정하며 JSON 형식의 경우는

```javascript
// 해당 step 이 추가됨
introJs().addStep({
    element: document.querySelectorAll('#test'),
    intro: 'test',
    position: 'test'
})
```

```javascript
introJs().start().nextStep();
```

시 두 번째 Step 부터 소개를 시작한다
반대로 previousStep() 을 호출하면 이전 Step 으로 돌아가는데

```javascript
introJs().goToStep(3).start().previousStep();
```

호출 시 두 번째 Step 부터 소개를 시작한다.

## exit

```javascript
introJs().exit()
```

호출 시 소개를 종료한다.

## setOption

introJs 만의 고유한 객체를 보유하고 있는데,

```javascript
// test 라는 key 의 value 로 test 를 삽입함
introJs().setOption("test","test")

// setOptions 옵션을 주면 동시에 여러 객체를 선언할 수 있다.
introJs().setOptions({
    'test1':'test1',
    'test2':'test2'
})
```

## refresh

introJs 의 모든 설정이 끝난 후 순서를 재정렬 하고 싶을 때 사용한다.

```javascript
introJs().refresh()
```

## oncomplete & onexit & onchange

oncomplete 함수는 introJs 의 설명이 모두 끝난 후 사용할 콜백을 설정한다.

```javascript
introJs().oncomplte(() => {
    alert('소개 끝!')
})
```

onexit 함수는 introJs 의 설명 도중 또는 끝나고 사용자가 종료를 선언했을 때 사용할 콜백을 설정한다

```javascript
introJs().onexit(() => {
    alert('소개를 종료함')
})
```

onchange 함수는 introJs 의 각 설명 부분이 넘어갈 때 사용할 콜백을 설정한다

```javascript
introJs().onchange(() => {
    alert('새 단계가 호출됨!')
})
```





