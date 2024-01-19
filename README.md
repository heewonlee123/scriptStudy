### 240119
# 코드구조
- use strict : 새롭게 제정된 ES5에서 새로운 기능이 추가되고 기존 기능 중 일부가 변경되었기에, 호환성 문제가 생길수 있어 ES5의 기본 모드에선 활성화되지 않도록 설계했음
- 최상단에 있어야 한다는 것 / 꼭 사용할 필요는 없음
  ```
  use strict
  // 이 코드는 모던한 방식으로 실행됩니다
  ```
- 변수(이름이 붙는 저장소 / let ,var)와 상수(변화하지 않는 변수 / const)
- 대문자 상수
  
  ```
  const COLOR_RED = "F00";
  const COLOR_GREEN = "0F0";
  const COLOR_BLUE = "00F";
  const COLOR_ORANGE = "#FF7F00";
  // 색상을 고르고 싶을 때 별칭을 사용할 수 잇게 되었습니다.
  let color = COLOR_ORANGE;
  ```
- 불린형 ( true / false )
- null : 값이 존재하지 않는, 비어있는, 알수 없는 값
- undefined : 변수 선언했지만, 값이 할당되지 않은 상태 (undefined, NaN
- typeof 연산자 : 자료형을 반환
- 문자형 변환 : String(value)
- 숫자형 변환 : Number(value)
- if else : 조건문
- 삼항 연산자 : 반환 값을 달리하려는 목적으로 만들어졌기에 나무 남발X
  ```
  let result = condition ? value1 : value2;
  // value1 (true) 일 경우 반환 , value2 (false) 일 경우 반환

  let result = (age > 18) ? true : false
  // 가독성을 위해 () 사용하는 것을 권유함
  ```
- 논리 연산자 : ||(OR) , &&(AND), !(NOT)
- nullish 병합 연산자 ?? 를 사용하면 짧은 문법으로 여러 피연산자 중 그 값이 확정되어있는 변수를 찾을 수 있음
- a ?? b / a 가 null 도 아니고 undefined 도 아니면 a 그 외의 경우는 b
- || : 첫 번째 truthy 값을 반환함
- ?? : 첫 번째 정의된 값을 반환 함
- 안전성 관련 이슈 때문에 ??는 &&나 ||와 함께 사용하지 못함
  ```
  let height = 0;

  alert(height || 100); //100
  alert(height ?? 100); //0
  ```
- switch 문 : 특정 변수를 다양한 상황에서 비교할 수 있게 해줌
  ```
  switch(x){
    case 'value1': //if(x === 'value1')
    ...
    [break]

    case 'value2': // if(x === 'value2')
    ...
    [break]

    default:
    ...
    [break]
  }
  ```

  
