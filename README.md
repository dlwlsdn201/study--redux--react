# Redux

## react-redux
### useSelecor() hook 함수를 사용하는 컴포넌트가 re-rendering 되는 기준
  상황) 부모 A 컴포넌트, 자식 B 컴포넌트가 있을 때 부모 컴포넌트 리렌더링 현상 발생  
    1) 부모 A 컴포넌트에서 useSelector() 을 사용하는 중, 자식 B 컴포넌트에서 reducer 함수로 인해 store 에 상태 변화가 발생하면 부모 A 컴포넌트가 reRendering 이 발생하였다. 
    2) 원인을 분석해본 결과, 만약 부모 A 컴포넌트에서 useSelector(state => state.automation) 으로 automation 에 대한 state 객체 전체를 불러오는 상태였는데, B 컴포넌트에서  state.automation 의 하위 계층 state 를 업데이트 함으로 인해 부모 A 컴포넌트도 reRendering 이 발생한 것이다.        
    3) 즉, useSelector(state => state.<state 객체>) 을 호출하는 컴포넌트에서 <state 객체> 을 기준으로 하위 계층에 state 변화가 발생하면, 해당 컴포넌트는 무조건 reRendering 되는 것이다.        
    4) 성능 저하를 방지하기 위해, useSelector() 을 사용할 경우 꼭 필요한 state 계층까지만 선언하여 사용하는 것이 좋을 것 같다.
