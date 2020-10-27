1. 리액트 하기 전에 자바스크립트를 먼저 공부해서 아래 글에 있는 내용을 알고 있어야함
https://medium.com/@violetboralee/react%EB%A5%BC-%EB%B0%B0%EC%9A%B0%EA%B8%B0-%EC%A0%84%EC%97%90-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%A0-javascript%EA%B8%B0%EC%B4%88-e0665f8cbee0

2. 리액트 프로젝트의 구성요소(참고: https://leehwarang.github.io/2019/08/20/react_setting.html)

- 리액트의 역할(https://reactjs.org/)
  * 리액트는 jsx syntax를 사용할수있다(안해도 된다고 함) -> https://reactjs.org/docs/react-without-jsx.html
    위의 글처럼 jsx는 사실 REACT.createElement(component, props, ...children)을 하는 syntactic sugar일 뿐이라, 안쓸수가 있다. 

- 바벨의 역할(https://babeljs.io/docs/en/)
es6 를 es5로


- 웹팩의 역할
리액트는 번들된 html을 로드함. 웹팩이 이러한 번들링을 함


- 읽어보기
- https://medium.com/@siddharthac6/getting-started-with-react-js-using-webpack-and-babel-66549f8fbcb8




3. React & Webpack 4 From Scratch - No CLI
https://www.youtube.com/watch?v=deyxI-6C2u4&ab_channel=TraversyMedia

    * 리액트는 React, React-dom으로 구성 
      * https://shplab.tistory.com/entry/%EB%AC%B4%EC%A0%9C#:~:text=React%20%EC%99%80%20React%20DOM%20%EC%9D%98,%EA%B2%83%EC%9D%84%20%EB%8F%84%EC%99%80%EC%A3%BC%EB%8A%94%20%EB%AA%A8%EB%8D%B8%EC%9D%B4%EB%8B%A4.
      * https://medium.com/react-native-seoul/react-%EB%A6%AC%EC%95%A1%ED%8A%B8%EB%A5%BC-%EC%B2%98%EC%9D%8C%EB%B6%80%ED%84%B0-%EB%B0%B0%EC%9B%8C%EB%B3%B4%EC%9E%90-02-react-createelement%EC%99%80-react-component-%EA%B7%B8%EB%A6%AC%EA%B3%A0-reactdom-render%EC%9D%98-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC-41bf8c6d3764


    * webpack(파일 묶기) , webpack-dev-server
    * babel: 리액트에사 클래스, 애로우 펑션 같은걸 쓰기 때문...



4. JSX란(https://reactjs.org/docs/introducing-jsx.html):
It is called JSX, and it is a syntax extension to JavaScript. We recommend using it with React to describe what the UI should look like. 
JSX Represents Objects
Babel compiles JSX down to React.createElement() calls.

```
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez',
};

const Hello = (props) => {
  console.log(props);
  return <h1>Hello, {formatName(user)}!</h1>;
  
}
const element = <Hello className="hello">hi</Hello>;

ReactDOM.render(element, document.getElementById('root'));

```

출력:
```
Object {
  children: "hi",
  className: "hello"
}
```

createElement함수는 대략
```
export function createElement(type, props, ...children) {
  // jsx 처리
  if (typeof type === "function") {
    return type.apply(null, [props, ...children]);
  }
  return { type, props, children };
}
``` 

이렇게 생겼다. 그래서 Hello같은 함수를 만나면, props, children을 apply를 통해서 다시 함수로 전달해주기때문에  const Hello = (props) => { } 이렇게 props를 받아오게 되는 구조

jsx는 생긴건 html이랑 비슷해도 본질적으론 자바스크립트이다. (jsx없이도 react사용 가능, jsx를 사용하면 좀더 편리한 것이고, 결국 babel이 모두 변환해주는것, 이것 때문에 React.createElement함수를 사용하기 위해 import React를 모든 스크립트에서 하고 있는것)

