# 라이브러리

## react에서 router 라이브러리를 사용하는 이유

1. 

## react-router-dom

1. 설치

   1. npm i react-router-dom

2. App.js에 import

   1. Import React, {Component} from 'react';
   2. Import { BrowserRouter,Router, Link,Switch } from "react-router-dom";

3. ```react
   <BrowserRouter>
        <Route path="/" exact component={Home}/>
        <Route path="/profile" exact component={Profile}/>
        <Route path="/profile/:id" component={Profile}/>
        <Route path="/about" component={About}/>
        <Route component={NotFound}/>
      </BrowserRouter>
   ```

4. BrowserRouter 

   1. history API를 사용해 URL과 UI를 동기화 하는 라우터.

5. Route

   1.  컴포넌트의 속성에 설정된 URL과 현재 경로가 일치하면 해당하는 컴포넌트, 함수를 렌더링 한다.
   2. path로 설정해 놓은 경로를 업데이트 하고 싶은 컴포넌트(props)와 연결한다 

6. Exact

   1. 경로가 중복되어서 두 개 이상의 컴포넌트가 동시에 렌더링 되는 것을 막는다.
   2. 위의 코드에서 profile 이라는 component가 두개 존재 할때 react-router-dom의 매칭 알고리즘에 의해서 두 경로가 정확하게 같을때만 Profile로 연결이 된다.
   3. 그렇기 때문에 아래의 /Prifile/:id 와 같이 /로 붙어서 다른경로를 가르키게 될 경우에 렌더링 시키지 않는다. 

7. Link 

   1.  'a'태그와 비슷하다, a 태그의 href의 역할을 to 속성이 한다. 서버에 갔다 오지 않고 링크로 이동한다, 기록이 history 스택에 저장됩니다.

8. ### Switch 

   1.  자식 컴포넌트 Route 또는 Redirect 중 매치되는 첫 번째 요소를 렌더링합니다. Switch를 사용하면 BrowserRouter만 사용할 때와 다르게 하나의 매칭되는 요소만 렌더링한다는 점을 보장해줍니다.

   2. 사용하지 않을 경우 매칭 되는 모두를 렌더링 합니다 .

   3. #### Switch 사용법

      1. 기존 방식의 경우 각 path와 component를 병렬로 평가해서 렌더링 한다 .
      2. 하지만 Switch 문을 사용할 경우 순차적으로 매칭시켜서 렌더링 한다 .
      3. <img width="511" alt="스크린샷 2020-12-16 오후 4 57 01" src="https://user-images.githubusercontent.com/75972718/102320589-daf93280-3fbf-11eb-889a-cd4bc3b5ab02.png">
      4. switch문의 특징은
         1. 각 비교문이 포함 관계에 있다면 순서에 따라 결과가 달라진다.
         2. 이게 어떤 의미냐면 /라는 경로는 /about의 포함관계이기 때문에 /라는 경로를 먼저 적어주고 뒤에 /about이라는 경로를 적어줘도 /about으로는 갈 수 없습니다 때문에 포함관계를 생각해서 경로를 작성해 줘야합니다.
         3. 위의 코드를 포함관계를 고려해서 작성하면 다음과 같습니다.
         4. <img width="511" alt="스크린샷 2020-12-16 오후 5 01 27" src="https://user-images.githubusercontent.com/75972718/102321040-78ecfd00-3fc0-11eb-8748-a218d165e693.png">
      5. 그리고 가장 마지막에 어떤 경로에도 매칭되는 Route를 하나 작성해 줍니다 .
         1. 그리고 NotFound.jsx파일을 하나 생성해 줍니다.
         2. <img width="1362" alt="스크린샷 2020-12-16 오후 5 08 29" src="https://user-images.githubusercontent.com/75972718/102321750-763ed780-3fc1-11eb-9b38-83e44f820f19.png">
         3. 위와 같은 방법으로 잘못된 경로에 대한 처리를 해 줄 수 있습니다.

9. ### Dynamic Routing (정해지지 않은 경로,라우팅)

10. #### Params 방식

    1. ex) Profile/1 과 같은 스타일, 이렇게 사용한다는건 1이 적힌자리에 어떤 숫자가 올지 모른다는 의미이고 어떤것이 들어와도 대응할 수 있어야 한다 .

    2. 순서는 URL 읽어서 뒤에 붙은 정보에 해당하는 유저를 저장해 놓은 어딘가에서 찾아 그에 맞는 페이지를 보여줘야 한다.

    3. 이때 저 1을 꺼내는 방법에 대해서 설명해 보겠습니다.

    4. 먼저 동일 경로에 exact 해주고 우리가 찾고자 하는 형태를 받아들일 라우터 설정을 아래와 같이 작성해줍니다.

    5. ​     <Route path="/profile/:id" component={Profile}/>

    6. 그 다음 우리가 /:id 를 찾아야되는 곳은 Profile 컴포넌트 이기 때문에 Profile.js로 가서 먼저 다음과 같이 props를 출력해 줍니다.

    7. <img width="389" alt="스크린샷 2020-12-16 오후 3 40 21" src="https://user-images.githubusercontent.com/75972718/102314066-24905000-3fb5-11eb-9a1f-817f0d4ccc15.png">

    8. props를 출력한 결과는 다음과 같이 3개의 property를 갖습니다.

    9. <img width="334" alt="스크린샷 2020-12-16 오후 3 42 07" src="https://user-images.githubusercontent.com/75972718/102314199-64573780-3fb5-11eb-92f1-5386d27f3d7e.png">

    10. 이 3개의 프로퍼티를 자세히 보기 위해 디스트럭처링 할당을 해서 출력해 보겠습니다.

    11. <img width="420" alt="스크린샷 2020-12-16 오후 3 44 35" src="https://user-images.githubusercontent.com/75972718/102314487-e182ac80-3fb5-11eb-87b2-4008a6163ed9.png">

    12. 다음과 같이 3개의 프로퍼티가 들어온다는 것은 react-router-dom이 내부적으로 다음과 같이 추가해줬다는 것을 의미합니다.

        1. ```react
           <Profile history ={{}} location={{}} match={{}}
           ```

    13. 다음으로 match의 params를 이용해서 아이디 값을 꺼내와 보겠습니다.

    14. <img width="1010" alt="스크린샷 2020-12-16 오후 3 51 22" src="https://user-images.githubusercontent.com/75972718/102314975-afbe1580-3fb6-11eb-801b-8f01a6f3dda2.png">

    15. 다음과 같은 방법으로 어떤 아이디 값을 가진 유저가 접근한지 알아낼 수 있고 이를 통해서 다음과 같이 조건부 렌더링을 해 줄 수 있습니다 .

    16. <img width="557" alt="스크린샷 2020-12-16 오후 3 56 33" src="https://user-images.githubusercontent.com/75972718/102315379-691ceb00-3fb7-11eb-9c91-e7ef3023259c.png">

    17. 이때 주의 해야할 점은 Profile/3에서 match.params로 꺼내온 Id 값의 타입은 string이다. 

    18. 그렇다면 About/?id=3과 같은 쿼리스트링은 어떤 방식으로 대응할 수 있을까?

11. #### 쿼리스트링 방식

    1. Params방식의 경우는 라우터 설정을 따로 해주었지만 쿼리 스트링 방식의 경우는 optional한 의미로 많이 쓰이기 때문에 없을땐 없고 있을땐 있는 방식으로 사용되기 때문에 따로 라우터 설정을 해주지 않습니다.
    2. params 방식과 마찬가지로 props를 출력해보면 다음과 같습니다.
    3. <img width="334" alt="스크린샷 2020-12-16 오후 3 42 07" src="https://user-images.githubusercontent.com/75972718/102314199-64573780-3fb5-11eb-92f1-5386d27f3d7e.png">
    4. 쿼리 스트링의 경우는 history와 location에 둘다 search안에 아이디 값이 존재합니다.
    5. <img width="319" alt="스크린샷 2020-12-16 오후 4 08 01" src="https://user-images.githubusercontent.com/75972718/102316387-2b20c680-3fb9-11eb-9a0d-83900487a079.png">
    6. 굳이 history에서 한단계 더 들어가지 않고 location에서 꺼내오면 다음과 같습니다.
    7. <img width="786" alt="스크린샷 2020-12-16 오후 4 11 39" src="https://user-images.githubusercontent.com/75972718/102316578-8652b900-3fb9-11eb-853f-eda8e5e20fb1.png">
    8. 이런 방식으로 오게되면 경로에 적힌 문자열이 오기 때문에 search.id와 같은 방식으로 접근해서 꺼내올 수 없습니다.
    9. 그렇다면 id 값을 어떻게 꺼내와야 할까요?
       1. String 메서드를 사용하는 방법
          1. <img width="790" alt="스크린샷 2020-12-16 오후 4 17 25" src="https://user-images.githubusercontent.com/75972718/102317083-52c45e80-3fba-11eb-8ebd-8df4788799fb.png">
          2. 이 방식의 경우 about?id=34&name=mark 와 같이 다른 문자열이 오게되면 걸러 낼 수 없기 때문에 유연하지 못합니다 .
          3. 여러 방법을 사용해서 걸러낼 순 있지만 복잡하기 때문에 위와같은 방법은 추천하지 않습니다. 
          4. 그렇다면 또 어떤 방법이 있을까요?
       2. New URLSearchParams를 이용하는 방법
          1. URLSearchParams는 URL의 쿼리 문자열에 대해 작업할수 있는 유틸리티 메서드를 말합니다 .
          2. <img width="812" alt="스크린샷 2020-12-16 오후 4 36 31" src="https://user-images.githubusercontent.com/75972718/102318632-ff9fdb00-3fbc-11eb-9c45-be4998f83a73.png">
          3. URLSearchParams는 객체 인스턴스를 반환하는데 public 하지 않기 때문에 메서드를 사용해서 꺼내와야합니다 . 
          4. <img width="985" alt="스크린샷 2020-12-16 오후 4 43 29" src="https://user-images.githubusercontent.com/75972718/102319272-f6fbd480-3fbd-11eb-8f4e-3c592fbf4208.png">
          5. 하지만 이 방법 역시 IE를 아예 지원하지 않는 단점이 존재한다 .
       3. 외부 라이브러리를 사용하는 방법(Query String)
          1. 라이브 러리를 사용할땐 검증된 라이브러리를 사용하는 것을 권장합니다.
          2. 설치
             1. npm i query-string
          3. <img width="985" alt="스크린샷 2020-12-16 오후 4 48 30" src="https://user-images.githubusercontent.com/75972718/102319730-aafd5f80-3fbe-11eb-8cb0-c298a66e6c26.png">
          4. 라이브러리를 사용하여 다음과 같은 방법으로 조건부 렌더링 해주면 됩니다.
          5. ![스크린샷 2020-12-16 오후 4.51.54](/Users/young/Library/Application Support/typora-user-images/스크린샷 2020-12-16 오후 4.51.54.png)

### 사실 지금까지의 과정만으로는 SPA라고 할 수 없다.

1. 우리가 기본적으로 사이트간 이동을 할때 li태그에 a태그를 활용하는데

2.  a태그의 기본 동작은 href의 적힌 URL을 바꿔주고 서버에 가서 페이지를 받아와서 로딩하는 서버사이드렌더링을 기본동작으로 하기때문에 SPA라고 할 수 없습니다.

3. 그렇기 때문에 a 태그가 아닌 Link태그를 사용해야하고 href속성도 to라는 속성으로 바꿔서 작성해 줘야합니다.

4. <img width="485" alt="스크린샷 2020-12-16 오후 5 30 17" src="https://user-images.githubusercontent.com/75972718/102323952-82786400-3fc4-11eb-9b0d-bc5054fe9e3e.png">

5. 이 Link 태그가 하는 일은 history API를 사용해서 URL을 바꿔주고 Switch문 내부의 경로를 따라 서버에 갔다 오지 않고 렌더링만 바꿔줍니다 .

6. Link로 작성된 코드는 아래와 같이 실제 DOM에는 a태그로 나오지만 Link 컴포넌트가 내부적으로 a태그의 기본 동작을 바꿔줌으로써 클라이언트 사이드 렌더링을 할 수 있게됩니다.

7. <img width="350" alt="스크린샷 2020-12-16 오후 5 33 37" src="https://user-images.githubusercontent.com/75972718/102324277-f87ccb00-3fc4-11eb-9c35-beb518263d1f.png">

8.  NavLink를 사용하면 Link와 동일하게 동작하지만 추가적으로 몇가지를 더 할 수 있습니다 

   1. <img width="332" alt="스크린샷 2020-12-16 오후 5 44 01" src="https://user-images.githubusercontent.com/75972718/102325387-6c6ba300-3fc6-11eb-89db-03e5048b728d.png">
   2. <img width="238" alt="스크린샷 2020-12-16 오후 5 44 29" src="https://user-images.githubusercontent.com/75972718/102325442-7d1c1900-3fc6-11eb-9cc8-29b311aef3aa.png">
   3. activeClassName, activeStyle 처럼 active 상태에 대한 스타일 지정이 가능합니다.
   4. Route의 Path 처럼 동작하기 때문에 exact가 있습니다 . 

   