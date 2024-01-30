![image]
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
- break 문이 없는 경우에는 조건에 부합하는지 여부를 따지지 않고 이어지는 case문을 실행함
  ```
  let a = 2 + 2;

  switch (a) {
    case 3:
      alert( '비교하려는 값보다 작습니다.' );
    case 4:
      alert( '비교하려는 값과 일치합니다.' );
    case 5:
      alert( '비교하려는 값보다 큽니다.' );
    default:
      alert( "어떤 값인지 파악이 되지 않습니다." );
  }
  ```
- 함수 선언
  ```
  // 함수 선언문
  function showMessage(){
    alert('안녕하세요');
  }

  // 매개변수를 차례로 써주면서 함수 선언
  function name(parameter1, parameter2, ... parameterN){
    //함수 본문
  }

  showMessage();

  // 지역 변수 : 함수 내에서 선언한 변수
  function showMessage(){
    let message ="안녕하세요";
    alert( message );
  }
  
  showMessage(); // 안녕하세요
  alert( message ); // message 함수 내 지역 변수라 defined 뜸

  // 외부 변수
  let userName = 'John'; // 전역 변수 : 이름을 가진 지역 변수에 의해 가려지지만 않으면 모든 함수에 접근 가능

  function showMessage() {
    userName = "Bob"; // (1) 외부 변수를 수정함
  
    let message = 'Hello, ' + userName;
    alert(message);
  }
  
  alert( userName ); // 함수 호출 전이므로 John 이 출력됨
  
  showMessage();
  
  alert( userName ); // 함수에 의해 Bob 으로 값이 바뀜
  
  // 매개변수
  function showMessage(from, text) { // 인자: from, text
    alert(from + ': ' + text);
  }
  
  showMessage('Ann', 'Hello!'); // Ann: Hello! (*)
  showMessage('Ann', "What's up?"); // Ann: What's up? (**)

  // if (text === undefined) 조건을 준 것과
  function showMessage(from, text) {
  if (text === undefined) {
    text = 'no text given';
  }
  alert( from + ": " + text );
  }

  // || 연산자로 조건을 준 것과 같음
  function showMessage(from, text) {
  // text의 값이 falsy면 기본값이 할당됨
  // 이 방식은 text == ""일 경우, text에 값이 전달되지 않은것과 같다고 간주합니다..
  text = text || 'no text given';
  }

  // 매개변수 'count'가 `undefined` 또는 `null`이면 'unknown'을 출력해주는 함수
  function showCount(count) {
    alert(count ?? "unknown");
  }
  
  showCount(0); // 0
  showCount(null); // unknown
  showCount(); // unknown

  function showPrimes(n) {

  for (let i = 2; i < n; i++) {
    if (!isPrime(i)) continue;

    alert(i);  // a prime
    }
  }

  function isPrime(n) {
    for (let i = 2; i < n; i++) {
      if ( n % i == 0) return false;
    }
    return true;
  }
  
  ```
- 화살표 함수 기본 ㅣ 함수 표현식보다 단순하고 간결한 문법으로 만들 수 있음
  ```
  let func = (arg1, arg2, ...argN) => expression

  let func = function(arg1, arg2, ...argN) {
    return expression;
  };

  // 인수가 하나도 없을 땐 괄호를 비워놓으면 됩니다. 다만, 이 때 괄호는 생략할 수 없습니다.
  let sayHi = () => alert("안녕하세요!");

  sayHi();
  
  ```

- alert, prompt, confirm을 이용한 상호작용
  - alert : 작은 창은 모달 창이라고 부름
  - prompt : 브라우저에서 제공하는 prompt 함수는 두 개의 인수를 받습니다
    ```
      result = prompt(title, [default]);
  
    ```
  - confirm : question(질문) 과 확인 및 취소 버튼이 있는 모달 창을 보여줌

- 객체 : 여덟 가지 자료형이 있음
  ```
  let user = new Object(); // '객체 생성자' 문법
  let user = {};  // '객체 리터럴' 문법
  
  ```
- 리터럴과 프로퍼티
  ```
  let user = {     // 객체
    name: "John",  // 키: "name",  값: "John"
    age: 30,       // 키: "age", 값: 30
    "likes birds": true  // 복수의 단어는 따옴표로 묶어야 합니다.
  };

  let user = {};
  // set
  user["likes birds"] = true;
  
  // get
  alert(user["likes birds"]); // true
  
  // delete
  delete user["likes birds"];

  let user = {
  name: "John",
  age: 30
  };

  let key = "likes birds";

  // user["likes birds"] = true; 와 같습니다.
  user[key] = true;

  let key = prompt("사용자의 어떤 정보를 얻고 싶으신가요?", "name");
  
  // 변수로 접근
  alert( user[key] ); // John (프롬프트 창에 "name"을 입력한 경우)

  let obj = {
  0: "test" // "0": "test"와 동일합니다.
  };
  
  // 숫자 0은 문자열 "0"으로 변환되기 때문에 두 얼럿 창은 같은 프로퍼티에 접근합니다,
  alert( obj["0"] ); // test
  alert( obj[0] ); // test (동일한 프로퍼티)

  "key" in object // 연산자 in 을 사용하면 프로퍼티 존재 여부를 확인할 수 있음

  let user = { name: "John", age: 30 };
  
  alert( "age" in user ); // user.age가 존재하므로 true가 출력됩니다.
  alert( "blabla" in user ); // user.blabla는 존재하지 않기 때문에 false가 출력됩니다.
  
  ```
- for...in 반복문
  ```
  for (key in object) {
    // 각 프로퍼티 키(key)를 이용하여 본문(body)을 실행합니다.
  }
  ```
- 참조에 의한 객체 복사
  - 객체는 '참조에 의해' 저장되고 복사된다는 것
  - 원시값은 '값 그대로' 저장, 할당되고 복사됨
  ```
  let user = { name: 'John' };

  let admin = user;
  
  admin.name = 'Pete'; // 'admin' 참조 값에 의해 변경됨
  
  alert(user.name); // 'Pete'가 출력됨. 'user' 참조 값을 이용해 변경사항을 확인함
  ```
  - 객체 비교 시 동등 연산자 == 와 일치 연산자 === 는 동일하게 동작합니다.
  - 객체를 복제하고 싶은 경우
    ```
      let user = {
        name: "John",
        age: 30
      };
      
      let clone = {}; // 새로운 빈 객체
      
      // 빈 객체에 user 프로퍼티 전부를 복사해 넣습니다.
      for (let key in user) {
        clone[key] = user[key];
      }
      
      // 이제 clone은 완전히 독립적인 복제본이 되었습니다.
      clone.name = "Pete"; // clone의 데이터를 변경합니다.
      
      alert( user.name ); // 기존 객체에는 여전히 John이 있습니다.

      // Object.assign를 사용하는 방법
      Object.assign(dest, [src1, src2, src3...])

      let user = { name: "John" };
      let permissions1 = { canView: true };
      let permissions2 = { canEdit: true };

      // permissions1과 permissions2의 프로퍼티를 user로 복사합니다.
      Object.assign(user, permissions1, permissions2);
      // now user = { name: "John", canView: true, canEdit: true }

      let user = {
        name: "John",
        size: {
          height: 182,
          width: 50
        }
      };

      let clone = Object.assign({}, user);
      
      user.sizes.width++; // 한 객체에서 프로퍼티를 변경합니다.
      alert(clone.sizes.width); // 51, 다른 객체에서 변경 사항을 확인할 수 있습니다.
    
    ```
- 옵셔널 체이닝 ( 스펙에 추가된 지 얼마 안 된 문법, 구식 브라우저는 폴리필:브라우저에서 지원하지 않는 코드를 사용 가능한 코드조각이나 플러그인으로 변환한 코드를 의미함 이 필요함)
  - ?.은 ?.'앞'의 평가 대상이 undefined 나 null 이면 평가를 멈추고 undefined 를 반환합니다.
    ```
      let user = {};

      alert( user?.address?.street); // undefined, 에러가 발생하지 않습니다.
    ```
- 원시값의 메서드
  - 원시형의 종류 : 문자, 숫자, bigint, 불린, 심볼, null, undefined
    ```
      let john = {
        name: "John",
        sayHi: function() {
          alert("친구야 반갑다!");
        }
      };
      
      john.sayHi(); // 친구야 반갑다!
    ```
- 배열 : 키를 사용해 식별할 수 있는 값을 담은 컬렉션은 객체라는 자료구조를 이용해 저장함
  ```
  let arr = new Array();
  let arr = [];
  ```
  - 큐 : 배열을 사용해 만들 수 있는 대표적인 자료구조 / push : 맨 끝에 요소 추가 shift : 제일 앞 요소를 꺼내 제거한 후 남아있는 요소들을 앞으로 밀어줌 
    ![image](https://github.com/heewonlee123/scriptStudy/assets/108706556/8376d095-f91d-4ef5-b102-71336360d766)
  - 스택 : 한쪽 끝에 요소를 더하거나 뺄 수 있게 해주는 자료구조 / push : 요소를 스택 끝에 집어넣기 pop : 스택 끝 요소를 추출함
    ![image](https://github.com/heewonlee123/scriptStudy/assets/108706556/1d01dff0-9c39-4f4c-ae9c-d02b19332d3b)
  - 요소 추가·제거 메서드
    - arr.push(...items) – 맨 끝에 요소 추가
    - arr.pop() – 맨 끝 요소 제거
    - arr.shift() – 맨 앞 요소 제거
    - arr.unshift(...items) – 맨 앞에 요소 추가
      ```
        let arr = ["I", "study", "JavaScript"];

        arr.splice(1, 1); // 인덱스 1부터 요소 한 개를 제거
        
        alert( arr ); // ["I", "JavaScript"]
      ```
      - concat : 기존 배열의 요소를 사용해 새로운 배열을 만들거나 기존 배열에 요소를 추가할 때 사용 함
      - forEach
        ```
        arr.forEach(function(item, index, array) {
          // 요소에 무언가를 할 수 있습니다.
        });
        ```
      - 배열 탐색
        ```
          let arr = [1, 0, false];
          
          alert( arr.indexOf(0) ); // 1
          alert( arr.indexOf(false) ); // 2
          alert( arr.indexOf(null) ); // -1
          
          alert( arr.includes(1) ); // true
        ```
      - find , findIndex
        ```
          let result = arr.find(function(item, index, array) {
            // true가 반환되면 반복이 멈추고 해당 요소를 반환합니다.
            // 조건에 해당하는 요소가 없으면 undefined를 반환합니다.
          });

          let users = [
            {id: 1, name: "John"},
            {id: 2, name: "Pete"},
            {id: 3, name: "Mary"}
          ];
          
          let user = users.find(item => item.id == 1);
          
          alert(user.name); // John
        ```
      - map ( 유용성과 사용 빈도가 아주 높은 메서드 중 하나)
       ```
         let result = arr.map(function(item, index, array) {
            // 요소 대신 새로운 값을 반환합니다.
          });

         let lengths = ["Bilbo", "Gandalf", "Nazgul"].map(item => item.length);
         alert(lengths); // 5,7,6
       ```
       - sort(fn) : 배열의 요소를 정렬해줌
         ```
          let arr = [ 1, 2, 15 ];

          // arr 내부가 재 정렬됩니다.
          arr.sort();
          
          alert( arr );  // 1, 15, 2
         ```
       - reverse : arr의 요소를 역순으로 정렬시켜주는 메서드
         ```
          let arr = [1, 2, 3, 4, 5];
          arr.reverse();
          
          alert( arr ); // 5,4,3,2,1
         ```
       - split과 join
         ```
          let names = 'Bilbo, Gandalf, Nazgul';

          let arr = names.split(', ');
          
          for (let name of arr) {
            alert( `${name}에게 보내는 메시지` ); // Bilbo에게 보내는 메시지
          }
         ```
        요소를 더하거나 지우기

        - push(...items) – 맨 끝에 요소 추가하기
        - pop() – 맨 끝 요소 추출하기
        - shift() – 첫 요소 추출하기
        - unshift(...items) – 맨 앞에 요소 추가하기
        - splice(pos, deleteCount, ...items) – pos부터 deleteCount개의 요소를 지우고, items 추가하기
        - slice(start, end) – start부터 end 바로 앞까지의 요소를 복사해 새로운 배열을 만듦
        - concat(...items) – 배열의 모든 요소를 복사하고 items를 추가해 새로운 배열을 만든 후 이를 반환함. items가 배열이면 이 배열의 인수를 기존 배열에 더해줌
        
        원하는 요소 찾기
        
        - indexOf/lastIndexOf(item, pos) – pos부터 원하는 item을 찾음. 찾게 되면 해당 요소의 인덱스를, 아니면 -1을 반환함
        - includes(value) – 배열에 value가 있으면 true를, 그렇지 않으면 false를 반환함
        - find/filter(func) – func의 반환 값을 true로 만드는 첫 번째/전체 요소를 반환함
        - findIndex는 find와 유사함. 다만 요소 대신 인덱스를 반환함
        
        배열 전체 순회하기
        
        - forEach(func) – 모든 요소에 func을 호출함. 결과는 반환되지 않음
        
        배열 변형하기
        
        - map(func) – 모든 요소에 func을 호출하고, 반환된 결과를 가지고 새로운 배열을 만듦
        - sort(func) – 배열을 정렬하고 정렬된 배열을 반환함
        - reverse() – 배열을 뒤집어 반환함
        - split/join – 문자열을 배열로, 배열을 문자열로 변환함
        - reduce(func, initial) – 요소를 차례로 돌면서 func을 호출함. 반환값은 다음 함수 호출에 전달함. 최종적으로 하나의 값이 도출됨
     
  - iterable 객체 : 반복 가능한 객체는 배열을 일반화한 객체입니다. 이터러블 이라는 개념을 사용하면 어떤 객체에든 for..of 반복문을 적용할 수 있습니다.
    ```
    let range = {
      from : 1,
      to : 5
    };
    // 1. for..of 최초 호출 시, Symbol.iterator가 호출됩니다.
    range[Symbol.iterator] = function(){
    // Symbol.iterator는 이터레이터 객체를 반환합니다.
    // 2. 이후 for..of는 반환된 이터레이터 객체만을 대상으로 동작하는데, 이때 다음 값도 정해집니다.
      return {
        current: this.from,
        last: this.to,
      
        // 3. for..of 반복문에 의해 반복마다 next()가 호출됩니다.
        next(){
          if(this.current <= this.last){
            return { done: false, value: this.current++ };
          } else{
            return { done : true };
          }
        }
      };
    };

    // 이제 의도한 대로 동작합니다
    for (let num of range) {
      alert(num);
    }
    ```
    let arrayLosl = {
      0: "Hello",
      1: "World",
    };


  
