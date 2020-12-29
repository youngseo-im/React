# 기본 Hook 3가지

## useState

- 먼저 useState란 상태 값과 그 값을 갱신하는 함수를 반환하는 것을 말합니다.

- 최초로 렌더링 하는 동안, 반환된 state(state)는 첫 번째 전달된 인자(initialState)의 값과 같습니다.

- setState 함수는 state를 갱신할 때 사용합니다. 새 state의 값을 받아 컴포넌트 리렌더링을 큐에 등록합니다.

- 다음 리렌더링 시에 useState를 통해 반환받은 첫 번째 값은 항상 갱신된 최신 state가 됩니다.

- **주의** 

  - React는 setState함수 동일성이 안정적이고 리렌더링 시에도 변경되지 않을 것이라는 것을 보장합니다. 이것이 useEffect나 useCallback 의존성 목록에 이 함수를 포함하지 않아도 무방한 이유입니다.

- ### useState 사용법1

  - 카운트 버튼을 누르면 숫자가 하나씩 올라가는 예제를 작성해보겠습니다 코드는 다음과 같습니다.
  - <img width="480" alt="스크린샷 2020-12-29 오후 8 26 21" src="https://user-images.githubusercontent.com/75972718/103280671-502f2380-4a14-11eb-8d8d-1a2124b0bb19.png">
  - 렌더링된 결과물은 다음과 같이 click 버튼을 누를때 마다 카운터에 1씩더 해지는걸 확인할 수 있습니다.
  - <img width="491" alt="스크린샷 2020-12-29 오후 8 28 27" src="https://user-images.githubusercontent.com/75972718/103280793-9b493680-4a14-11eb-8902-13ae579bfc83.png">
  - 이렇게 useState를 이용해서 초기 렌더링시에는 초기값 0이 나오게되고
  - 버튼이 클릭됐을땐 setCount함수가 호출되서 state의 값이 갱신되면서 리렌더링되기때문에 
  - count는 늘 최신의 state값을 갖게됩니다.
  - 또 useState는 여러개 선언될 수 있습니다.

- ### useState 사용법 2

  - 만약 State라는 커다란 컴포넌트 내부에서 state들을 가지고있고 그걸 가져와서 사용하는 경우는 다음과 같이 사용해야합니다.
  -  <img width="607" alt="스크린샷 2020-12-29 오후 8 53 25" src="https://user-images.githubusercontent.com/75972718/103282132-18c27600-4a18-11eb-9924-ef915106b31e.png">
  - 또 setState같은 경우에는 static한 값이 바뀔 땐 객체로 작성하는 경우가 문법적으로 맞고
  - 데이터를 조작해서 새로운 값으로 만들어줄 때는 보통 함수형으로 작성해줍니다.

## useEffect

- 이 부분은 [저번 포스팅][https://github.com/youngseo-im/React/blob/master/%ED%81%B4%EB%9E%98%EC%8A%A4%20%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%9D%98%20%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0%EC%99%80%20Hooks%EC%9D%98%20useEffect.md]에서 클래스 컴포넌트의 생명주기와 useEffect를 비교한 내용에 포함되어 있으므로 생략.

## useContext

- useContext는 context 객체(React.createContext에서 반환된 값)을 받아 그 context의 현재 값을 반환합니다.

- context의 현재 값은 트리 안에서 이 Hook을 호출하는 컴포넌트에 가장 가까이에 있는 <MyContext.Provider>의 value prop에 의해 결정됩니다.

- 컴포넌트에서 가장 가까운 MyContext.Provider가 갱신되면 이 Hook은 MyContext.provider에게 전달된 가장 최신의 context value를 사용하여 렌더러를 트리거 합니다.

- 상위 컴포넌트에서 React.memo 또는 shouldComponentUpdate를 사용하더라도 useContext를 사용하고 있는 컴포넌트 자체에서부터 다시 렌더링 됩니다 .

- 쉽게 얘기하면 useContext는 하위 컴포넌트 전체에 데이터를 공유하는 방법으로 사용됩니다.

- 데이터를 set하는 곳은

  - 가장 상위 컴포넌트 => Provider

- 데이터를 get하는 곳은

  - 모든 하위 컴포넌트에서 접근이 가능하고 방법은 아래와 같이 3가지가 있습니다.
  - Consumer로 하는 방법
  - Class component의 this.context로 하는 방법
  - Functional component의 useContext로 하는 방법

- ### useContext 사용법

  - 제일 먼저 context를 생성해 줍니다.
  - <img width="515" alt="스크린샷 2020-12-29 오후 9 58 15" src="https://user-images.githubusercontent.com/75972718/103285308-24ff0100-4a21-11eb-98b8-732080e47333.png">
  - <img width="709" alt="스크린샷 2020-12-29 오후 9 59 30" src="https://user-images.githubusercontent.com/75972718/103285376-52e44580-4a21-11eb-8710-ddb304e97521.png">
  - 그 후에 다음과 같이 index.js에 가장 상위 컴포넌트에 이와 같이 set 해줍니다.
  - 그렇게 되면 저 PersonContext.Provider안에있는 하위 컴포넌트들에게는 직접 props를 주지않아도
  - 저 persons의 값들을 가져다 쓸 수 있게 됩니다.
  - 데이터를 get하는 방법은 다음과 같습니다.
  - **Consumer를 사용하는 경우**
    - <img width="591" alt="스크린샷 2020-12-29 오후 10 12 10" src="https://user-images.githubusercontent.com/75972718/103286124-187ba800-4a23-11eb-8284-edecaaac48cc.png">
  - **Class component사용하는 경우**
    - <img width="561" alt="스크린샷 2020-12-29 오후 10 20 21" src="https://user-images.githubusercontent.com/75972718/103286732-3c8bb900-4a24-11eb-932f-05f344d56390.png">
  - **function component를 사용하는 경우**
    - <img width="536" alt="스크린샷 2020-12-29 오후 10 26 28" src="https://user-images.githubusercontent.com/75972718/103287140-187ca780-4a25-11eb-989e-55ae70084b01.png">
  - 결과물
    - <img width="285" alt="스크린샷 2020-12-29 오후 10 26 56" src="https://user-images.githubusercontent.com/75972718/103287167-27fbf080-4a25-11eb-927b-3854941c9226.png">