Intro.JS

해당 저장소는 <a src="https://introjs.com/docs/">introjs</a> 공식 홈페이지 를 참고하여 만들어졌음을 밝힙니다.

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
