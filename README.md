# movie-app

React JS Fundementals Course

**pre-requirement**

- npm, npx, nodejs
- npx create-react-app 명령어로 우리가 만들 react app에 필요한 패키지들을 한방에 설치 가능!

**React 작동 방식**

- App.js의 App 함수에서 return 값으로 <div>hello</div>를 하면 화면에 hello가 나온다.
- index.js에서 App 함수에서 작성한 태그들을 document.getElementById("root") 객체 안에 넣는다. 즉 index.html에 있는 id=root인 태그 안에 App.js에서 작성한 태그를 넣는다.
- react는 html 문서에 처음부터 모든 태그를 넣지 않고 태그를 더하거나 빼는 방법을 코드로 작성할 수 있게 해준다!
- 앱을 실행할 때 내용이 없는 html을 보여주고 react가 js파일에서 작성해둔 html 내용들을 비어있는 html에 넣는다.
  -> virtual DOM
