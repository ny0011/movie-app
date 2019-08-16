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

**Creating your first React Component**

ReactDOM.render(<App />, document.getElementById("potato"));
에서 <App />은 이전에 보던 html태그 형식이 아님.

- <App /> : component. react는 component로 동작함. 모든 것은 component! 그냥 App만 쓰면 에러 발생함.
- component? : HTML을 반환하는 함수.
- -> javascript와 html이 혼합된 형태 : jsx(react의 고유 특성)

- 나만의 component를 만들어보자!

1. Potato.js 파일을 만든다
2. **import React from "react";** 라고 첫줄에 react를 가져온다. 그래야 react가 이 함수를 이해할 수 있음
3. 그리고 파일 이름과 같게 Potato() 함수를 만들고 생성할 태그를 리턴한다
4. 외부에서 Potato() 함수를 사용하려면 export default Potato; 라고 정의한다
5. index.js에서 import Potato from "./Potato" 로 가져오고 ReactDOM 내부에 <App /> 옆에 <Potato />라고 써본다
   -> 안됨!
   -> **react app은 component 하나만 render로 사용함!** 그게 App이 되었음.
6. App.js안에 Potato()함수를 사용해보자
7. import Potato from "./Potato"를 App.js로 가져오고 h1 태그 밑에 <Potato /> 라고 써본다
8. 웹페이지를 실행하면 Potato() 함수가 실행되었다..!
