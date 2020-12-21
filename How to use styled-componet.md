# Styled-Component

1. 새로운 프로젝트 생성하기.
   1. npx create-react-app styled-components-example
   2. Cd styled-components-example
2. 설치
   1. npm install --save styled-components
3. 먼저 생성된 프로젝트의 App.js에 다음과 같이 입력해 준 후에 npm start로 서버를 열어서 확인합니다.
   1. <img width="366" alt="스크린샷 2020-12-21 오후 1 13 44" src="https://user-images.githubusercontent.com/75972718/102738784-81fa1780-438e-11eb-81b0-592d64727dfb.png">
   2. 그럼 다음과 같은 결과가 나타납니다.
   3. <img width="494" alt="스크린샷 2020-12-21 오후 1 15 38" src="https://user-images.githubusercontent.com/75972718/102738888-c7b6e000-438e-11eb-888e-78e680b6e963.png">
   4. 이렇게 styled-components를 사용하면 해당 스타일을 가진 컴포넌트를 만들어낼 수 있습니다 .
   5. 그렇다면 styled-components의 장점은 뭐가 있을까요?

## styled-component의 장점

1. 클래스를 만들 필요가 없습니다.
   1. 위의 코드와 같이 해당스타일을 가진 컴포넌트를 만들어내기 때문에 따로 클래스를 지정해줄 필요가 없습니다.
2. CSS 파일이 필요 없습니다.
   1. 1번의 이유와 같은 이유로 css 파일을 만들지 않고 스타일을 지정합니다.
3. 컴포넌트 자체에서 스타일을 포함하고 있기 때문에 재사용에 용의합니다.

## styled-component 문법 익히기

1. 먼저 아까 코드의 5번째 줄을 확인해보면 styled.div`` 와 같은 형태로 작성이 되어 있습니다.

2. 이때 뒤에 붙은 div는 HTML Element를 의미 하기 때문에 div를 스타일링 하고싶다면 styled.div, input을 스타일링 하고 싶다면 styled.input과 같은 형태로 사용 하면 됩니다.

3. 이번에는 아까 만든 Circle 컴포넌트에 color 라는 props를 넣어줘 보겠습니다.

4. <img width="991" alt="스크린샷 2020-12-21 오후 1 42 04" src="https://user-images.githubusercontent.com/75972718/102740151-79a3db80-4392-11eb-801c-f219a143c0d6.png">

5. 이런식으로 Circle 컴포넌트에 props를 넣어주고 props가 존재하는 경우 props.color값을 배경값으로 사용하고 그렇지 않으면 black으로 사용하도록 설정되었습니다.

6. 이번에는 huge라는 props를 설정됐을 때 크기를 더 키워서 보여주도록 작업을 해보겠습니다.

7. <img width="987" alt="스크린샷 2020-12-21 오후 1 49 06" src="https://user-images.githubusercontent.com/75972718/102740537-73622f00-4393-11eb-899f-3f769a8a707e.png">

8. 이런식으로 여러 줄의 css 코드를 조건부로 보여주고 싶다면 css를 import해서 사용해야 합니다.

9. ### Button 만들기

   1. 지금부터는 재사용성 높은 Button 컴포넌트를 styled-component로 구현해보도록하겠습니다.
   2. 먼저 src안에 components 디렉토리를 생성한 후 그 안에 Button.jsx 파일을 생성하세요.
   3. <img width="466" alt="스크린샷 2020-12-21 오후 1 55 35" src="https://user-images.githubusercontent.com/75972718/102740940-5da13980-4394-11eb-82c4-08865b2a4849.png">
   4. 다음은 App.js에서 Button을 사용해봅시다.
   5. <img width="961" alt="스크린샷 2020-12-21 오후 1 59 35" src="https://user-images.githubusercontent.com/75972718/102741154-ec15bb00-4394-11eb-8aab-fd039d70b173.png">
   6. 다음은 Sass의 lighten, darken 과 같은 유틸 함수를 사용하기 위해 polished라는 라이브러리를 설치해 주겠습니다.
   7. **npm install --save polished**
   8. 그럼 기존의 색상 부분을 polished의 유틸 함수들로 대체 해보겠습니다.
   9. <img width="371" alt="스크린샷 2020-12-21 오후 2 11 02" src="https://user-images.githubusercontent.com/75972718/102741739-84606f80-4396-11eb-9908-c315334f8a0f.png">
   10. 그럼 이번엔 회색, 핑크색 버튼들을 만들어볼건데요, 색상 코드를 지닌 변수를 Button.jsx에서 선언을 하는 대신에 [ThemeProvider][https://styled-components.com/docs/api#themeprovider]라는 기능을 사용해서 styled-components로 만드는 모든 컴포넌트에서 조회하여 사용 할 수 있는 전역적인 값을 설정해보겠습니다.
   11. App.js를 다음과 같이 수정해보세요.
   12. <img width="513" alt="스크린샷 2020-12-21 오후 2 18 41" src="https://user-images.githubusercontent.com/75972718/102742155-97277400-4397-11eb-9a0f-da0aa8f37f77.png">
   13. 이렇게 theme을 설정하면 ThemeProvider 내부에 렌더링된 styled-components로 만든 컴포넌트에서 palette를 조회하여 사용 할 수 있습니다. 한번 Button 컴포넌트에서 우리가 방금 선언한 palett.blue 값을 조회해봅시다.
   14. <img width="415" alt="스크린샷 2020-12-21 오후 2 23 28" src="https://user-images.githubusercontent.com/75972718/102742446-419f9700-4398-11eb-92c8-497c70205e8d.png">
   15. ThemeProvider로 설정한 값은 styled-components에서 props.theme으로 조회 할 수 있습니다, 지금은 selected의 값을 무조건 blue값을 가르키게 했는데 이부분을 Button 컴포넌트가 color props를 통하여 받아오게 될 색상을 사용하도록 수정해보겠습니다.
   16. <img width="466" alt="스크린샷 2020-12-21 오후 2 30 27" src="https://user-images.githubusercontent.com/75972718/102742877-66e0d500-4399-11eb-8f2b-c882e5949bcc.png">
   17. 현재 props.color의 값이 undefined 이기 때문에 defaultProps를 지정해줍니다.
   18. <img width="551" alt="스크린샷 2020-12-21 오후 2 32 49" src="https://user-images.githubusercontent.com/75972718/102743012-c8a13f00-4399-11eb-856f-eaf8d3edcc9e.png">
   19. 지금은 기본 색상이 blue가 되도록 설정해주었습니다.
   20. 이제 App 컴포넌트를 열어서 회색, 핑크색 버튼을 렌더링 해봅시다.
   21. <img width="1021" alt="스크린샷 2020-12-21 오후 2 36 54" src="https://user-images.githubusercontent.com/75972718/102743119-246bc800-439a-11eb-90a0-8a5edce86c91.png">
   22. Button 컴포넌트의 코드는 다음과 같이 디스트럭처링 할당을 통해 리팩토링 할 수 있습니다.
       1. <img width="420" alt="스크린샷 2020-12-21 오후 2 42 05" src="https://user-images.githubusercontent.com/75972718/102743469-db684380-439a-11eb-9b44-b833abd52f47.png">
   23. 다음으로는 size props를 설정해서 버튼의 크기를 다양하게 만들어 보겠습니다.
   24. 코드의 가독성을 위해 코드를 아래와 같이 분리해주고 StyledButton에 넣어줍니다.
       1. <img width="346" alt="스크린샷 2020-12-21 오후 2 53 20" src="https://user-images.githubusercontent.com/75972718/102744132-6e55ad80-439c-11eb-8fef-1e8c93e746fc.png">
       2. <img width="278" alt="스크린샷 2020-12-21 오후 2 54 14" src="https://user-images.githubusercontent.com/75972718/102744189-8decd600-439c-11eb-9e1b-b68cb2cff8d0.png">
   25. 다음은 App.js로 돌아와서 커스터마이징된 버튼들을 렌더링해봅시다.
   26. <img width="465" alt="스크린샷 2020-12-21 오후 2 58 46" src="https://user-images.githubusercontent.com/75972718/102744442-300cbe00-439d-11eb-8f03-bc15b800e12d.png">
       1. 이 과정에서 ButtonGroup이라는 컴포넌트를 만들어서 서로간의 여백을 1rem으로 설정해주었습니다.
       2. 렌더링된 모습은 다음과 같습니다.
       3. <img width="568" alt="스크린샷 2020-12-21 오후 2 59 01" src="https://user-images.githubusercontent.com/75972718/102744465-3864f900-439d-11eb-9f2e-bfc3722e3cad.png">
   27. 위와 같이 여러 색들을 지닌 버튼들이 나타났나요?
   28. 다음은 방금 작성한 sizeStyles의 중복되는 코드를 리팩토링 하면 다음과 같습니다.
       1. <img width="318" alt="스크린샷 2020-12-21 오후 3 08 22" src="https://user-images.githubusercontent.com/75972718/102745022-86c6c780-439e-11eb-8d66-729df707c476.png">
       2. size도 color와 마찬가지로 undefined이기때문에 defaultProps를 설정해줍니다
       3. <img width="230" alt="스크린샷 2020-12-21 오후 3 08 35" src="https://user-images.githubusercontent.com/75972718/102745037-8d553f00-439e-11eb-9436-2e3527af7ec3.png">
   29. 다음에는 Button 컴포넌트에 outline이라는 props를 설정하여 이 값이 true 일 때에는 테두리만 지닌 버튼을 보여주도록 설정해보겠습니다. 이 작업을 할 때에는 colorStyles만 수정해주면 됩니다.
       1. <img width="423" alt="스크린샷 2020-12-21 오후 3 32 57" src="https://user-images.githubusercontent.com/75972718/102746607-f68a8180-43a1-11eb-88e9-3fc3d4b48e32.png">
       2. <img width="567" alt="스크린샷 2020-12-21 오후 3 41 55" src="https://user-images.githubusercontent.com/75972718/102747231-369e3400-43a3-11eb-96e0-258da01eaa05.png">
       3. App.js에 outline props를 추가해줍니다.
       4. <img width="583" alt="스크린샷 2020-12-21 오후 3 33 15" src="https://user-images.githubusercontent.com/75972718/102746649-0bffab80-43a2-11eb-86cc-bf1402d5e579.png">
       5. 렌더링된 화면은 다음과 같습니다.
       6. <img width="350" alt="스크린샷 2020-12-21 오후 4 15 50" src="https://user-images.githubusercontent.com/75972718/102749781-f3928f80-43a7-11eb-8a51-43535ea60b0e.png">
   30. 이제 Button 컴포넌트에서 해야 할 마지막 작업이 한가지 더 남았습니다. fullWidth라는 props가 주어졌다면 버튼의 크기가 100%를 차지하도록 만들어 보세요.
       1. Button 컴포넌트에 다음과 같이 코드를 작성해 줍니다
       2. <img width="325" alt="스크린샷 2020-12-21 오후 4 53 13" src="https://user-images.githubusercontent.com/75972718/102752629-2be89c80-43ad-11eb-9d44-f8a0eecb7cfb.png">
       3. 그 다음 StyledButton에 추가해줍니다
       4. <img width="376" alt="스크린샷 2020-12-21 오후 4 53 54" src="https://user-images.githubusercontent.com/75972718/102752691-4c185b80-43ad-11eb-8aed-cdb98f562133.png">
       5. 그 다음엔 Button 함수 컴포넌트에 넣어줍니다.
       6. <img width="674" alt="스크린샷 2020-12-21 오후 4 54 59" src="https://user-images.githubusercontent.com/75972718/102752790-74a05580-43ad-11eb-99f3-d2790b330cab.png">
       7. 그럼 다음과 같이 렌더링이 됩니다.
       8. <img width="573" alt="스크린샷 2020-12-21 오후 4 52 23" src="https://user-images.githubusercontent.com/75972718/102752524-0fe4fb00-43ad-11eb-9e97-23f7b87bd63d.png">
   31. ㅇ

10. ㅇ





