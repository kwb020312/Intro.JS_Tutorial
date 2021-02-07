Intro.JS

## 설치

```HTML
<script src="https://cdnjs.cloudflare.com/ajax/libs/intro.js/3.2.1/intro.min.js"></script>
```

```javascript
npm install intro.js --save
```

Git 을 통해서도 사용이 가능하나 업데이트가 늦어지는 편, 권장하지 않는다.

## 주 명령어

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
