---
title: 리엑트 프로젝트 셋업방법
date: 2021-05-12 21:30:33
tags: [react, javascript]
categories: [react, javascript]
---

---

# 리엑트 프로젝트 셋업방법

## create-react-app

create react app은 react를 배우기 위한 싱글 페이지 앱이다.  
이 앱을 설치함으로써 개발환경 구축, 최신 JS를 사용가능하고 앱 최적화를 해준다.  
create recat app 은 백 엔드 로직이나 DB를 제어할 수 없다.  
babel이나 webpack같은 빌드 도구를 사용하지만 설정 없이도 동작한다.  
npm run build 명령어만으로 쉽게 배포가 가능하다.  
[create react app Readme](https://github.com/facebook/create-react-app#create-react-app-)
우선 npx를 설치해 주는데 npx는 npm 5.2이상 버전의 패키지 실행 도구이다.

```
 npm i npx -g
```

설치한 npx로 create react app를 설치한다.

```
 npx create-react-app 프로젝트명
```

위의 명령어를 실행하면 실행한 경로에서 프로젝트명으로 폴더를 생성하여 리엑트 연습환경으로 셋팅을 해준다.

---

## baseUrl 설정

jsconfig.json 파일을 package.json과 같은 경로에 생성하여 아래와 같이 생성해준다.

```javascript
{
  "compilerOptions": {
    "baseUrl": "src"
  }
}
```

이전에는 이 설정을 `.env`파일에 해주었다고 하는데 강제로 변경되었다고 한다.  
여기서 설정해주는 `baseUrl`의 의미는 js파일에서 import를 할 경우 상대경로로 한다면 추후 매우 복잡하게 경로가 표시되는데 절대경로의 기준이 되는 폴더를 설정해주는 것이다.  
package.json 파일과 같은경로에 두는 이유는 src경로 밖에 있어야 하기 때문이다.

---

## prop-types 설치

```
  npm install prop-types
```

위의 명령어를 이용해 prop-types을 설치해준다.
prop-types는 컴포넌트에 들어온 값이 유효한 값인지 prop의 type를 미리 정의해준다. 이로인해 잘못된 입력을 막을 수 있다.

---

```
npm start
```

위의 명령어를 입력하면 리엑트 프로젝트가 localhost의 3000번 포트에서 실행된다.

---

## React Router

```
npm install react-router-dom
```

react-router-dom을 설치해준다.  
React Router는 react에서 사용하는 route 패키지로 dom이나 react native에서 사용 가능하다.  
Route의 JAVA기반의 웹페이지로 비교하면 컨트롤러와 비슷한 역할을 한다고 볼 수 있다.
리엑트는 위에서 설명한것처럼 싱글 페이지 앱(SPA)으로 url입력시 매번 새로고침 되면서 모든 페이지를 호출하는것이 아니라 Router를 사용하여 변경된 소스만 바꿔주도록 되어있어 부드럽고 빠르다.

```javascript
export default () => (
  <Router>
    <Switch>
      <Route path="/" exact component={Home} />
      <Route path="/tv" exact component={TV} />
      <Route path="/search" exact component={Search} />
      <Redirect from="*" to="/" />
    </Switch>
  </Router>
);
```

Router를 사용할 경우 위와같은 코드를 짤 수 있는데 URL과 매칭되는 Path 값에 따라 컴포넌트를 연결해준다.  
즉 사용자가 URL로 요청을 하면 Router에서 이를 제어해준다.
Router중 많이 사용되는것이 2가지 있는데 BrowserRouter, HashRouter 이다.  
HashRouter는 배포가 쉽고 새로고침을 해도 에러가 나지 않지만 검색엔진이 찾지 못하고 주소에 #이 붙어 불편하다.  
BrowserRouter는 새로고침시 에러가 발생하는 문제가 있지만 검색엔진이 찾을 수 있고 HTML5 history API를 활용할 수 있으며 동적인 페이지에서 유용하다.

---

## switch

위의 코드를 보면 Switch가 있는걸 볼 수 있다.
Switch의 역할은 path를 통해 1가지 이상의 경로가 같이들어올때의 문제를 해결한다.  
예를들어 요청하지 않은 url을 호출할 경우를 대비해 예외처리 페이지를 만들었다면 없는 url을 입력했을때 해당 페이지만 처리되어야 한다.  
하지만 모든 url은 /를 포함하게 되어있고 이는 메인페이지 이기 때문에 둘이 같이 출력되게 되어있다.  
이럴때 Switch를 사용하게 되면 첫번째로 매칭되는 path의 컴포넌트만 호출하기 때문에 정상적으로 처리가 가능하다.
이 외에도 위에 표시된것처럼 exact를 사용하게 되면 정확하게 일치하는 path만 호출하도록 하는것도 가능하다.

---

## React에서의 CSS

리엑트에서 CSS는 일반적인 HTML에서와 같은방식의 작업도 가능은 하지만 컴포넌트별로 관리하는 리엑트에서 글로벌하게 사용하는 일반적인 css사용은 하지않는것이 좋다.  
create-react-app은 local 스코프에서 css를 동작시키도록 module.css를 지원하는데 파일명.module.css로 만들어주면 된다. 이 방법으로 css를 작성한다면 js파일에서 css파일을 import하여 변수처럼 css한 내용을 부여할 수 있다.
또 다른 방식은 styled-components를 사용하는 것이다.

```
npm install styled-components
```

위의 명령어로 설치해준다.

```javascript
import React from "react";
import { Link } from "react-router-dom";
import styled from "styled-components";

const List = styled.ul`
  display: flex;
  list-style-type: none;
  justify-content: space-around;
`;
const ReactLink = styled(Link)`
  text-decoration: none;
`;

export default () => (
  <header>
    <List>
      <li>
        <ReactLink to="/">Movies</ReactLink>
      </li>
      <li>
        <ReactLink href="/tv">TV</ReactLink>
      </li>
      <li>
        <ReactLink href="/search">Search</ReactLink>
      </li>
    </List>
  </header>
);
```

위의 코드가 styled-components 사용하여 작성한 css이다.
styled를 import하고 변수에 styled.ul변수로 선언한 css문을 넣어주고 기존의 ul태그를 변수명 List로 변경한다.
Link처럼 react router에서 제공하는 태그는 `(Link)`로 호출할 수 있다.
styled-components 사용함으로써 완벽하게 로컬에서만 사용되면서도 아예 js파일 안에서 같이 작성까지 할 수 있다.  
css파일을 나누고 class이름을 지어서 파일을 옮겨다니면서 맞춰주는 이런 귀찮은 작업들이 없어지기 때문에 굉장히 편하게 작업할 수 있다.
하지만 css가 생겨난것 자체가 재사용성을 늘리기 위해서 인데 로컬에서만 관리한다면 html에 style로 작업하는것과 다를것이 없기 때문에 글로벌하게 설정하는것도 가능하다.

```
npm install styled-reset
```

styled-reset을 설치해주는데 reset만 봐도 알 수 있듯이 html에 모든 태그들의 기본값들을 초기화 시켜주는것이다. 참고로 reset를 하는 이유는 브라우저마다 태그의 기본값들이 미세하게 다르기 때문에 표준을 지키기가 힘들다.

```javascript
const { createGlobalStyle } = require("styled-components");
const { reset } = require("styled-reset");

const globalStyles = createGlobalStyle`
    ${reset};
    a{
        text-decoration:none;
        color:inherit;
    }
    *{
        box-sizing:border-box;
    }
    body{
        font-size:13px;
        background-color:rgba(20,20,20,1);
    }
`;

export default globalStyles;
```

위에 코드처럼 global 스코프에서 사용할 css들을 정리해주고 이를 App.js에 라우터 아래에 넣어준다면 App.js에서 호출되는 모든 코드들은 모두 위의 스타일이 자동으로 적용될것이다.

---

## Axios

```
npm install axios
```

위의 명령어로 설치가 가능하다.  
axios는 HTTP 통신의 요구사항을 컴팩트한 패키지로써 사용하기 쉽게 설계 되었다.  
Axios의 인스턴스를 설정 해줄 수 있다는 점에서 좋다.  
우리는 Axios 인스턴스에 baseURL, timeout, headers 같이 여러곳에서 반복되는 것들을 한번만 정의해서 여러곳에서 사용이 가능하다.

```javascript
const { default: axios } = require("axios");

const api = axios.create({
  baseURL: "https://api.themoviedb.org/3/",
  params: {
    api_key: "apikey를 입력해준다.",
    language: "en-US",
  },
});

export default api;
```

위는 axios를 사용하는 코드인데 자주 사용할 api를 미리 정의해놓는 것이다.
api에서 데이터를 호출할때마다 url부터 api키를 다 입력해줘야 한다면 매우 비효율적이기 때문에 axios를 이용하여 한번만 정의하고 axios 인스턴스를 호출하여 사용하면 된다.

---

[셋팅하면서 작성한 코드 링크](https://github.com/fkfkfk999/react_app)
