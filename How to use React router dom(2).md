# React-route-dom(2)

## Javascript로 라우팅하기

1. 전 시간에는 JSX로 라우팅하는 방법을 알아봤으니 다음은 JS로 라우팅하는 방법에 대해서 알아보겠습니다 .
2. 먼저 Login.jsx 파일을 다음과 같이 Javascript로 페이지를 이동하는 코드를 작성해 만들어주고 App.js에 import를 해줍니다.
3. <img width="344" alt="스크린샷 2020-12-17 오전 1 20 29" src="https://user-images.githubusercontent.com/75972718/102375727-30583280-4006-11eb-8240-a49f88d317a9.png">
4. 위와 같은 방식은 서버 사이드 렌더링이기 때문에 우리가 추구하는 SPA의 역할을 수행하지 못하고 있습니다 그렇다면 클라이언트 사이드 렌더링을 하기 위해선 어떻게 해야할까요?
5. 먼저 인수로 props를 넣고 어떤 프로퍼티가 나오는지 살펴봅시다.
6. <img width="736" alt="스크린샷 2020-12-17 오전 1 22 02" src="https://user-images.githubusercontent.com/75972718/102375909-685f7580-4006-11eb-8cc1-e639b08dd376.png">
7. 위와 같은 방식으로 props를 받아와서 console.log를 찍어보면 history, location,match이 세가지 프로퍼티가 나오게되는데 
   1. match에 나오는 내용은 App.js에 작성된 Route의 Path와 URL에 나오는 경로와의 관계에대해 설명합니다 
      1. <img width="431" alt="스크린샷 2020-12-17 오전 1 25 51" src="https://user-images.githubusercontent.com/75972718/102376544-1834e300-4007-11eb-8f54-5d204198e188.png">
      2. isExact가 true 라는 것은 path와 URL의 경로가 일치했다는것을 의미합니다.
   2. location에 나오는 내용은 현재 위치에 대한 내용을 담고있습니다.
   3. history는 URL에 담긴 내용에 대해 설명하고 있습니다 .
8. 그렇다면 우리는 history API를 사용해서 그 안에 있는 Push를 통해 서버 로딩없이 URL만 바꿔치기해서 페이지를 변경해 줄 수 있겠죠
9. <img width="356" alt="스크린샷 2020-12-17 오후 5 17 51" src="https://user-images.githubusercontent.com/75972718/102461593-f03b9300-408b-11eb-938e-f2655b9831d2.png">
10. 이때 history API를 이용해서 URL을 바꿔치기해주고 클라이언트 사이드 렌더링을 해주는건 리액트의 역할이 되겠습니다 .
11. 그렇다면 이번에는 Button을 컴포넌트로 만들어서 렌더링을 시켜줘 보도록 하겠습니다 .
12. 먼저 component라는 폴더를 만들어준 후에 Button.jsx를 만들어줍니다 그리고 아까 만들어준 Login.jsx에 import를 해주고 버튼의 역할을 했던 함수 컴포넌트를 아까 Button.jsx로 옮겨주고 Login.jsx에는 JSX문법으로 버튼 컴포넌트를 넣어줍니다 .
13. <img width="971" alt="스크린샷 2020-12-17 오후 5 43 11" src="https://user-images.githubusercontent.com/75972718/102464250-7a392b00-408f-11eb-9e1d-d1f6bcd6ccda.png">
14. 이렇게 코드를 작성한 후에 렌더링 된 모습을 보면 ! 다음과 같이 에러가 납니다 ...! 
15. <img width="754" alt="스크린샷 2020-12-17 오후 5 43 52" src="https://user-images.githubusercontent.com/75972718/102464335-9210af00-408f-11eb-99b4-50cfdb02f8e4.png">
16. 그 이유는 바로 Login.jsx에 있는 Button 컴포넌트가 props를 받지 못했기 때문에 history에 있는 push를 찾지 못하기 때문인데요, 그렇기 때문에 Button 컴포넌트에 props를 다음과 같이 추가해줘야 합니다 .
17. <img width="361" alt="스크린샷 2020-12-17 오후 6 04 57" src="https://user-images.githubusercontent.com/75972718/102466564-85418a80-4092-11eb-819d-3a75dad29037.png">
18. 여기서 우리는 props의 history를 필요로 하기때문에 꼭 rest 파라미터로 풀어줘야 합니다 .
19. 풀지 않았을때 props = true의 값이 나오기 때문에!
20. 이렇게 하게되면 정상적으로 버튼을 눌렀을 때 2초후에 해당 경로로 이동되는것을 확인할 수 있습니다.
21. <img width="393" alt="스크린샷 2020-12-17 오후 6 10 38" src="https://user-images.githubusercontent.com/75972718/102467161-4f50d600-4093-11eb-8b42-3a4417253f98.png">
    <img width="393" alt="스크린샷 2020-12-17 오후 6 10 50" src="https://user-images.githubusercontent.com/75972718/102467186-5546b700-4093-11eb-91ca-6c4813a41485.png">
22. 지금은 Route => Login이라는 페이지 컴포넌트가 연결되어 있었고 Login 안에 Button이 존재했습니다 .
23. 그럼 만약에 Login => A => B => C => Button 이런식으로 존재한다면 Login에서 던져준걸 a,b,c는 Button 까지 전달만 하는 역할을 해야될때는 실수가 나오기 쉽습니다 때문에 이럴땐 컴포넌트를 다른 컴포넌트로 변환해주는 고차 컴포넌트를 사용해줍니다, 하지만 Hooks가 나오고 나서는 고차 컴포넌트의 역할을 Hooks가 대체하는 경우가 많습니다.
24. 하지만 고차 컴포넌트나 Hooks에 대한 자세한 얘기는 뒤쪽에 다루도록 하고 오늘은 고차 컴포넌트를 이런식으로 사용하는구나에 대한 맛 만 살짝 보도록 하겠습니다. 
25. 코드는 다음과 같습니다 .
26. <img width="437" alt="스크린샷 2020-12-17 오후 6 27 39" src="https://user-images.githubusercontent.com/75972718/102469104-afe11280-4095-11eb-9113-c8ec6b906b25.png">
27. 먼저 withRouter를 import 해주고, Button function에 export default를 떼줍니다 
28. 그후에 withRouter(Button)을 export default해줍니다 
29. 이 withRouter함수는 Button을 실행해줍니다.
30. 이 코드를 보면 Login에서 A,B,C 어떤게 있던간에 전달해주지 않고 그냥 withRouter가 실행한 Button의 결과물을 export default 해주는 역할을 합니다.
31. 이와 같은 과정으로 지금까지 계속 봐왔던 history, location, match는 Route에 연결된 component에만 들어간다는걸 알 수 있습니다.

### 다음은 Route props중 하나인 render 라는 props에 대해 알아보겠습니다.

1. 그동안 우리는 Route에 component를 딱 지정해서 렌더링을 해주었습니다 그럼 component와 render는 어떤 차이가 있을까요?
2. 먼저 코드를 작성해보면 다음과 같습니다.
3. <img width="456" alt="스크린샷 2020-12-17 오후 10 56 48" src="https://user-images.githubusercontent.com/75972718/102496851-4aa01800-40bb-11eb-913f-490c9b02f074.png">
4. 둘의 대략적인 차이는 component props는 그 컴포넌트가 실행되면서 인자로 props를 넣어주는 것이고 
5. render props 같은 경우는 props를 받아서 JSX 방식으로 리턴을 해줍니다 .
6. 그럼 render props가 언제 활용되는지 Login.jsx를 통해서 알아보도록 하겠습니다.
7. 먼저 , Redirect라는걸 알아야 하는데 이 역시 리액트 라우터에서 제공하는 기본 컴포넌트 입니다 .
8. Redirect의 역할은 요청 경로를 다른 경로로 redirection 합니다.
9. 먼저 코드를 보겠습니다 .
10. <img width="543" alt="스크린샷 2020-12-17 오후 11 14 55" src="https://user-images.githubusercontent.com/75972718/102498846-d1ee8b00-40bd-11eb-95d0-e7e86bc4fe6c.png">
11. 아직 인증을 배우지 않았기 때문에 isLogin이라는 변수를 하나 만들어서 true라는 값을 넣어둡니다 이 변수의 역할은 로그인이 됐다면 true, 되지 않았다면 false의 역할을 합니다 .
12. if문을 사용해서 만약 로그인이 된 상태라면 Redirect 의 to 속성을 이용해서 홈으로 보내주고 
13. 아니라면 Login 컴포넌트로 연결해서 로그인을 할 수 있도록 도와줍니다 .
14. 그럼 페이지로 돌아와서 login을 누르면 다음과 같이 뜹니다 .
15. <img width="332" alt="스크린샷 2020-12-17 오후 11 15 45" src="https://user-images.githubusercontent.com/75972718/102498934-ef235980-40bd-11eb-8fc3-78355d2b0fbf.png">
16. 이렇게 로그인을 눌러도 login 페이지로 렌더링이 옮겨지지 않지만 , 갔다왔다는것은 if문 위에있는 console.log를 통해서 알 수 있습니다 .
17. 그럼 isLogin 변수의 값을 false로 바꾼다면 다음과 같이 렌더링이 됩니다.
18. <img width="327" alt="스크린샷 2020-12-17 오후 11 17 19" src="https://user-images.githubusercontent.com/75972718/102499129-272a9c80-40be-11eb-9a22-c29bde74a5fd.png">
19. 이렇듯 component props의 경우는 컴포넌트 자체를 렌더링 해야하는 경우에 사용하고
20. Render props의 경우는 컴포넌트를 만들어 등록하는 것이 아니라 무엇을 보여 줄지 JSX문법을 사용해 리턴하는 방식으로 사용할 수 있습니다.

 