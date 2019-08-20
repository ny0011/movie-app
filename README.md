# movie-app

React JS Fundementals Course

**pre-requirement**

-   npm, npx, nodejs
-   npx create-react-app 명령어로 우리가 만들 react app에 필요한 패키지들을 한방
    에 설치 가능!

**React 작동 방식**

-   App.js의 App 함수에서 return 값으로 <div>hello</div>를 하면 화면에 hello가나
    온다.
-   index.js에서 App 함수에서 작성한 태그들을 document.getElementById("root") 객
    체 안에 넣는다. 즉 index.html에 있는 id=root인 태그 안에 App.js에서 작성한태
    그를 넣는다.
-   react는 html 문서에 처음부터 모든 태그를 넣지 않고 태그를 더하거나 빼는 방법
    을 코드로 작성할 수 있게 해준다!
-   앱을 실행할 때 내용이 없는 html을 보여주고 react가 js파일에서 작성해둔 html
    내용들을 비어있는 html에 넣는다. -> virtual DOM

**Creating your first React Component**

ReactDOM.render(<App />, document.getElementById("potato")); 에서 <App />은 이전
에 보던 html태그 형식이 아님.

-   <App /> : component. react는 component로 동작함. 모든 것은 component! 그냥
    App만 쓰면 에러 발생함.
-   component? : HTML을 반환하는 함수.
-   -> javascript와 html이 혼합된 형태 : jsx(react의 고유 특성)

-   나만의 component를 만들어보자!

1. Potato.js 파일을 만든다
2. **import React from "react";** 라고 첫줄에 react를 가져온다. 그래야 react가이
   함수를 이해할 수 있음
3. 그리고 파일 이름과 같게 Potato() 함수를 만들고 생성할 태그를 리턴한다
4. 외부에서 Potato() 함수를 사용하려면 export default Potato; 라고 정의한다
5. index.js에서 import Potato from "./Potato" 로 가져오고 ReactDOM 내부에
   <App /> 옆에 <Potato />라고 써본다 -> 안됨! -> **react app은 component 하나만
   render로 사용함!** 그게 App이 되었음.
6. App.js안에 Potato()함수를 사용해보자
7. import Potato from "./Potato"를 App.js로 가져오고 h1 태그 밑에 <Potato /> 라
   고 써본다
8. 웹페이지를 실행하면 Potato() 함수가 실행되었다..!

**2.1 Reusable Components with JSX + Props**

1. component로 html 문서를 작성할 수 있다
2. component에 정보를 보낼 수 있다. -> 동적으로 재사용할 수 있는 component를 사
   용할 수 있음!

-   App()에서 Food()로 인자를 전달하는 방법

1. App()함수에서 Food()를 호출할 때 다음처럼 작성함 : <Food fav="kimchi" />

-   <div class="kimchi"></div> 같은 형식으로 fav라는 property(특성)에 kimchi라는 value(값)로 인자 전달함
-   값은 {true}, {["hello",1,2,3,4,true]} bool값, Array값 등으로 여러가지 종류를
    가질 수 있음
-   property를 여러개로 줘도 Food()에서는 한 개의 인자에서 property를 Object형태
    로 모두 가져옴

2. Food()에서 fav prop만 가져오도록 할 때 : prop.fav 라고 해도 되지만 ES6 버전에
   서는 {fav}로 인자 설정을 해도 됨 -> Food({fav})
3. Food({fav})의 태그 내부에서 fav 변수 값을 사용할 때 : {fav} 라고 쓰면 됨.
4. Food(prop) -> {prop.fav}, Food({fav}) -> {fav}

**2.2 Dynamic Component Generation** 웹사이트에 동적 데이터를 추가해보자(API에서
받은 데이터를 웹사이트에 출력해본다)

1. 데이터를 받는다

-   foodLike, food들의 object 배열을 만든다(JSON 형식으로 받아온 데이터를 저장한
    배열 같음)

2. 함수를 만들자

-   map 함수(javascript 문법) :
    https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map

-   map함수로 받아온 데이터를 추출한다 return = array.map(function(element){
    return element + "ssssS" })

```
friends = ["aa","bb","Cc","dd"]
결과 = friends.map(배열의 원소 => {
    console.log(원소); // 데이터 처리
    return 원소; // 처리한 데이터를 리턴하면 그 데이터를 배열로 만들어서 결과 변수에 리턴함
})
```

-   App() 함수에서 받아온 데이터 배열을 map함수로 처리한다. 태그 안에서 자바 스
    크립트 문법을 사용하려면 {} 괄호 안에서 쓰면 됨.
-   데이터 배열의 오브젝트 dish를 Food() 함수의 인자로 보낼 때 dish 변수의 요소
    들을 보낼 수 있다. foodILike 배열이 key-value 형식이니까 dish.name,
    dish.image로 표현해서 각 요소의 값을 보냄.

```
{foodILike.map(dish => (
        <Food name={dish.name} picture={dish.image} />
      ))}
```

-   Food() 함수의 인자는 App()에서 보낸 name, picture과 이름이 같게 해서 함수 내
    에서 사용함.
-   img src 옆에 alt prop은 장님을 위해 설명글을 써달라는 prop. warning msg가 떠
    서 수정한건데 이 msg는 create-react-app 가 알려주는 것임.
-   https://stackoverflow.com/questions/43812733/what-does-this-warning-message-mean-img-elements-must-have-an-alt-prop-either

```
function Food({ name, picture }) {
  return (
    <div>
      <h3>I like {name}</h3>
      <img src={picture} alt="" />
    </div>
  )
```

-   {console.log(foodILike.map(renderFood))} 로 map이 반환하는 값이 Array임을 확
    인할 수 있다.
-   warning msg 발생. <Food />에서 warning 발생함. 생성된 Array의 원소들은 고유
    키 값을 가져야 함(?) -> map함수를 사용할 때 발생하는 메시지 같음..
-   map으로 태그의 리스트를 생성할 때 key값을 고유값으로 직접 지정해줘야 하나봄
-   https://stackoverflow.com/questions/28329382/understanding-unique-keys-for-array-children-in-react-js/43892905#43892905
-   map으로 새로운 배열을 만들면 unique key prop가 사라지나봄.. -> data array인
    foodILike에 id property를 추가해주자

```
Warning: Each child in a list should have a unique "key" prop.

```

-   데이터 배열에 추가한 id를 Food함수를 부르는 곳에서 key값에 넣어준다
-   key는 Food()함수로 넘기지 않음. react 내부에서 사용하는 key prop인가봄..

```
return <Food key={dish.id} name={dish.name} picture={dish.image} />;
```

**2.4 Protection with PropTypes**

-   props 간에 값을 전달할 때 제대로 받았는지 확인하고 싶음
-   아래 props-types 패키지를 설치하자
-   https://www.npmjs.com/package/prop-types

```
$ npm i props-types
```

-   내가 전달받은 prop이 내가 원하던 prop인지 확인해주는 패키지임
-   props-types 사용법

1. 사용할 js 파일에 import PropTypes from "prop-types"; 이라고 추가한다
2. 값을 받는 함수에 .propTypes = {} 를 추가한다
3. {} 안에 name: PropTypes.string.isRequired, 같이 name변수가 받을 타입을 지정해
   두면 된다.
4. 만약에 다른 타입이 들어왔으면 아래와 같은 에러가 발생함

```
index.js:1375 Warning: Failed prop type: Invalid prop `rating` of type `number` supplied to `Food`, expected `string`.
    in Food (at App.js:60)
    in App (at src/index.js:5)
```
