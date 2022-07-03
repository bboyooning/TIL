## 목차
  - [프로그래밍](#프로그래밍)
  - [자바스크립트](#자바스크립트)
  - [변수](#변수)
  - [표현식과 문](#표현식과-문)
  - [데이터 타입](#데이터-타입)
  - [연산자](#연산자)
  - [제어문](#제어문)
  - [타입 변환과 단축 평가](#타입-변환과-단축-평가)
  - [객체](#객체)
  - [원시 값과 객체의 비교](#원시-값과-객체의-비교)
  - [함수](#함수)
  - [스코프](#스코프)
  - [전역 변수의 문제점](#전역-변수의-문제점)
  - [let, const 키워드와 블록 레벨 스코프](#let,-const-키워드와-블록-레벨-스코프)
  - [프로퍼티 어트리뷰트](#프로퍼티-어트리뷰트)
  - [생성자 함수에 의한 객체 생성](#생성자-함수에-의한-객체-생성)
  - [함수와 일급 객체](#함수와-일급-객체)
  - [프로토타입](#프로토타입)
  - [빌트인 객체](#빌트인-객체)
  - [this](#this)
  - [실행 컨텍스트](#실행-컨텍스트)
  - [클로저](#클로저)
  - [클래스](#클래스)
  - [ES6](#ES6)
  - [배열](#배열)
  - [이터러블](#이터러블)
  - [스프레드 문법](#스프레드-문법)
  - [디스트럭처링 할당](#디스트럭처링-할당)
  - [set 과 Map](#set-과-Map)
  - [브라우저의 렌더링 과정](#브라우저의-렌더링-과정)
  - [DOM](#DOM)
  - [이벤트](#이벤트)
  - [타이머](#타이머)
  - [비동기 프로그래밍](#비동기-프로그래밍)
  - [Ajax](#Ajax)
  - [REST API](#Rest-API)
  - [프로미스](#프로미스)
  - [제너레이터와 async/await](#제너레이터와-async/await)
  - [Error](#Error)
  - [모듈](#모듈)
  - [Babel 과 Webpack](#Babel-과-Webpack)<br>

[뒤로](https://github.com/bboyooning/TIL)



## 객체

- 자바스크립트는 객체 기반의 프로그래밍 언어
- 자바스크립트를 구성하는 거의 ‘모든 것'이 객체
- 원시 값을 제외한 나머지 값(함수, 배열, 정규 표현식 등)은 모두 객체
- 원시 타입은 단 하나의 값만 나타내지만, 객체 타입은 다양한 타입의 값(원시 값 또는 다른 객체)을 하나의 단위로 구성한 복합적인 자료구조
- 원시 값은 변경이 불가능 하지만 객체 타입의 값, 즉 객체는 변경 가능한 값
- 객체는 0개 이상의 프로퍼티로 구성된 집합이며, 프로퍼티는 키와 값으로 구성됨

```jsx
var person = {
	name: "Lee",
	age: 20
}
```

- 자바스크립트에서 사용할 수 있는 모든 값은 프로퍼티 값이 될 수 있음
- 자바스크립트의 함수는 일급 객체 이므로 값으로 취급할 수 있음<br>
( * 일급객체? 다른 객체들에 일반적으로 적용 가능한 연산을 모두 지원하는 객체 )<br>
따라서 함수도 프로퍼티 값으로 사용할 수 있음
- 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해 이를 `메서드` 라고 부름

```jsx
var counter = {
	num: 0, // 프로퍼티
	increase: function (){ // 메서드
		this.num++;
	}
};
```

- 이처럼 객체는 `프로퍼티`와 `메서드`로 구성된 집합체
    - `프로퍼티` : 객체의 상태를 나타내는 값(data)
    - `메서드` : 프로퍼티(상태 데이터)를 참조하고 조작할 수 있는 동작
- 객체는 객체의 상태를 나타내는 값(프로퍼티)과 프로퍼티를 참조하고 조작할 수 있는 동작(메서드)을 모두 포함할 수 있기 때문에 <br> 상태와 동작을 하나의 단위로 구조화할 수 있어 유용
<br>

### 객체 리터럴에 의한 객체 생성

- 자바스크립트는 프로토타입 기반 객체지향 언어로서 다양한 객체 생성 방법을 지원
    - 객체 리터럴
    - Object 생성자 함수
    - 생성자 함수
    - Object.create 메서드
    - 클래스(ES6)
- 객체 생성 방법 중에서 가장 일반적이고 간단한 방법이 `객체 리터럴` 을 사용하는 방법
- 리터럴? 사람이 이해할 수 있는 문자 또는 약속된 기호를 사용하여 값을 생성하는 표기법
- 객체 리터럴? 객체를 생성하기 위한 표기법
- 객체 리터럴은 중괄호({…}) 내에 0개 이상의 프로퍼티를 정의
변수에 할당되는 시점에 자바스크립트 엔진은 객체 리터럴을 해석하여 객체를 생성함
- 만약 중괄호 내에 프로퍼티를 정의하지 않으면 빈 객체 생성
- 객체 리터럴의 중괄호는 코드 블록을 의미하지 않음! 따라서 코드 블록을 닫는 중괄호 뒤에는 세미콜론을 붙이지 않음
- 하지만 객체 리터럴은 값으로 평가되는 표현식이므로, 객체 리터럴의 닫는 중괄호 뒤에는 세미콜론을 붙인다.
- 객체 리터럴은 자바스크립트의 유연함과 강력함을 대표하는 객체 생성 방식
- 객체 리터럴에 프로퍼티를 포함시켜 객체를 생성함과 동시에 프로퍼티를 만들 수도 있고, 객체를 생성한 이후 프로퍼티를 동적으로 추가할 수도 있음
- 객체 리터럴 외의 객체 생성 방식은 모두 함수를 사용해 객체를 생성
<br>

### 프로퍼티

- 객체는 프로퍼티의 집합이며, 프로퍼티는 키와 값으로 구성
- 프로퍼티를 나열할 때는 쉼표(,)로 구분. 일반적으로 마지막 프로퍼티 뒤에는 쉼표를 사용하지 않으나 사용해도 상관없음

```jsx
var minsu = {
  name: '민수변수', // 프로퍼티 키: name, 프로퍼티 값: '민수변수'
  age: 200 // 프로퍼티 키: age, 프로퍼티 값: 200
};
```

- 프로퍼티 키와 값으로 사용할 수 있는 값은 다음과 같음
    - 프로퍼티 키 : 빈 문자열을 포함하는 모든 문자열 또는 심벌 값
    - 프로퍼티 값 : 자바스크립트에서 사용할 수 있는 모든 값
- 프로퍼티 키는 프로퍼티 값에 접근할 수 있는 이름으로서 식별자 역할을 함
- 심벌 값도 프로퍼티 키로 사용할 수 있지만 일반적으로 문자열을 사용. 이때 프로퍼티 키는 문자열이므로 따옴표(’…’ or “…”)로 묶어야 함
- 식별자 네이밍 규칙을 따르면 생략 가능 / 따르지 않으면 반드시 따옴표 사용
    - 식별자 네이밍 규칙
        - 반드시 문자로 시작
        - 1~30까지만 지정 가능
        - A~Z까지의 대소문자, 0~9까지의 숫자, 특수기호는 _, $, #만 가능
        - 오라클에서 사용되는 예약어 사용 불가
        - 다른 객체명에서 사용중인 것과 중복 불가
        - 공백 사용 불가
- 식별자 네이밍 규칙을 따르지 않는 프로퍼티 키를 사용하면 번거롭기 때문에 가급적 식별자 네이밍 규칙을 준수하는 프로퍼티 키를 사용할 것을 권장
- 문자열 또는 문자열로 평가할 수 있는 표현식 사용해 프로퍼티 키를 동적으로 생성 가능. 이 경우에는 프로퍼티 키로 사용할 표현식을 대괄호([…])로 묶어야 함  
- 빈 문자열을 프로퍼티 키로 사용해도 에러나지 않음
- 프로퍼티 키에 문자열이나 심벌 값 외의 값을 사용하면 암묵적 타입변환을 통해 문자열이 됨.<br>예를 들어, 프로퍼티 키로 숫자 리터럴을 사용하면 따옴표 붙지 않지만 내부적으로 문자열로 변환됨
- var, function 과 같은 예약어를 프로퍼티 키로 사용해도 에러 발생하지 않음<br>하지만 예상치 못한 에러가 발생할 여지가 있어 권장하지 않음
- 이미 존재하는 프로퍼티 키를 중복 선언하면, 나중에 선언한 프로퍼티가 먼저 선언한 프로퍼티를 덮어씀. 에러 발생하지 않으니 주의!
<br>

### 메서드

- 자바스크립트에서 사용할 수 있는 모든 값은 프로퍼티 값으로 사용할 수 있음
- 자바스크립트의 함수는 (일급)객체 이므로 값으로 취급할 수 있어 프로퍼티 값으로 사용가능
- 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위하여 `메서드` 라고 부름
- `메서드` 는 객체에 묶여 있는 함수를 의미함
    
    ```jsx
    var counter = {
    	num: 0, // 프로퍼티
    	increase: function (){ // 메서드
    		this.num++; // this 는 counter 객체를 가리킴
    	}
    };
    ```
    
- 메서드 내부에 사용한 `this` 키워드는 객체 자신을 가르키는 참조변수
<br>

### 프로퍼티의 접근

- 프로퍼티 접근 방법
    - 마침표 프로퍼티 접근 연산자(.)를 사용하는 `마침표 표기법`
    - 대괄호 프로퍼티 접근 연산자([…])를 사용하는 `대괄호 표기법`
- 프로퍼티 키가 식별자 네이밍 규칙을 준수하는, 즉 자바스크립트에서 사용 가능한 유효한 이름이라면 마침표 표기법과 대괄호 표기법 모두 사용할 수 있음
- 이 두 가지 방법의 좌측에는 객체로 평가되는 표현식을 기술, 마침표 프로퍼티 접근 연산자 우측 또는 대괄호 프로퍼티 접근 연산자 내부에는 프로퍼티 키 지정
- 대괄호 표기법 사용하는 경우, 대괄호 프로퍼티 접근 연산자 내부에 지정하는 프로퍼티 키는 반드시 ‘’ `따옴표` 로 감싼 문자열이어야 함! <br>
따옴표로 감싸지 않은 이름을 프로퍼티 키로 사용하면 자바스크립트 엔진은 식별자로 해석
- 프로퍼티 키가 식별자 네이밍 규칙을 준수하지 않는 이름
- 즉 자바스크립트에서 사용 가능한 유효한 이름이 아니면 `반드시` `대괄호 표기법`을 사용해야 함
- 단, 프로퍼티 키가 숫자로 이뤄진 문자열인 경우 따옴표 생략할 수 있고, 대괄호 내에 들어가는 프로퍼티 키는 반드시 따옴표로 감싼 문자열이어야 함
- ex)

```jsx
var person = {
	'last-name': 'Lee',
	1: 10
};

person.'last-name';  // SyntaxError: Unexpected string
person.last-name;    // 브라우저 환경: NaN
                     // Node.js 환경: ReferenceError: name is not defined
person[last-name];   // ReferenceError: last is not defined
person['last-name']; // Lee

// 프로퍼티 키가 숫자로 이뤄진 문자열인 경우 따옴표 생략 가능
person.1;    // SyntaxError: Unexpected number
person.'1';  // SyntaxError: Unexpected string
person[1];   // 10 : person[1] -> person['1]
person['1']; // 10
```

- person.last-name 실행 결과는 node.js 환경에서 참조오류 이고, 브라우저에선 NaN
- person.last-name 실행할 때, 자바스크립트 엔진은 먼저 person.last 를 평가함.
person 객체에서는 프로퍼티 키가 last 인 프로퍼티가 없기 때문에 undefined 로 평가됨<br>
따라서 person.last-name 은 undefined-name 과 같다.<br>
다음으로 자바스크립트 엔진은 name 이라는 식별자를 찾는다. 이때 name 은 프로퍼티 키가 아닌 식별자로 해석된다. 

- Node.js 환경에서는 현재 어디에도 name 이라는 식별자(변수, 함수 등의 이름) 선언이 없으므로 <br> ReferenceError: name is not defined 에러가 발생함

- 그러나 브라우저 환경에서는 name 이라는 전역 변수(전역 객체 window의 프로퍼티)가 암묵적으로 존재함. 
- 전역 변수 name 은 window 의 이름을 가르키며, 기본값은 빈 문자열임.따라서 person.last-name 은 undefined-’’와 같으므로 NaN 이 됨
<br>

### 프로퍼티 값 갱신

- 이미 존재하는 프로퍼티에 값을 할당하면 프로퍼티 값이 갱신됨<br>
이미 person 이란 객체에 name 프로퍼티가 존재하므로 name 프로퍼티의 값이 갱신됨
   
<br>

### 프로퍼티 동적 생성

- 존재하지 않는 프로퍼티에 값을 할당하면 프로퍼티가 동적으로 생성되어 추가되고 프로퍼티 값이 할당됨 <br>
person 객체에 age 프로퍼티 존재하지 않으므로, person 객체에 age 프로퍼티가 동적으로 생성되고 갑이 할당됨
   
<br> 

### 프로퍼티 삭제

- delete 연산자는 객체의 프로퍼티를 삭제함
- 이때 delete 연산자의 피연산자는 프로퍼티 값에 접근할 수 있는 표현식이어야 함<br>
만약 존재하지 않는 프로퍼티를 삭제하면 아무런 에러 없이 무시됨
- person 객체에 age 프로퍼티를 동적으로 생성한 후, delete 연산자로 age 프로퍼티 삭제<br>
address 프로퍼티는 존재하지 않아서 삭제할 수 없다. 하지만 에러는 발생하지 않음!
    
<br>

### ES6에서 추가된 객체 리터럴의 확장 기능

### 프로퍼티 축약 표현

- 객체 리터럴의 프로퍼티는 프로퍼티 키와 값으로 구성됨
- 프로퍼티 값은 변수에 할당된 값, 즉 식별자 표현식 일수도 있음
- ES6 에서는 프로퍼티 값으로 변수를 사용하는 경우, 변수 이름과 프로퍼티 키가 동일한 이름일 때 프로퍼티 키를 생략할 수 있음<br>
이때 프로퍼티 키는 변수 이름으로 자동 생성됨
<br>

### 계산된 프로퍼티 이름

- 문자열 또는 문자열로 타입 변환할 수 있는 값으로 평가되는 표현식을 사용하여 프로퍼티 키를 동적으로 생성할 수도 있음 <br>
단, 프로퍼티 키로 사용할 표현식을 대괄호([…])로 묶어야 함. 이를 `계산된 프로퍼티 이름` 이라고 함
- ES5 에서 계산된 프로퍼티 이름으로 프로퍼티 키를 동적 생성하려면 객체 리터럴 외부에서 대괄호([…]) 표기법을 사용해야 함
- ES6 에선 객체 리터럴 내부에서도 계산된 프로퍼티 이름으로 프로퍼티 키를 동적 생성 가능
<br>

### 메서드 축약 표현

- ES5에서 메서드를 정의하려면 프로퍼티 값으로 함수를 할당
- ES6에서 메서드를 정의할 때 function 키워드를 생략한 축약 표현 사용 가능
- ES6의 메서드 축약 표현으로 정의한 메서드는 프로퍼티에 할당한 함수와 다르게 동작함
→ ES6 사양에서 메서드는 메서드 축약 표현으로 정의된 함수만을 의미한다
    
    ```jsx
    const obj = {
      x: 1,
      foo() { return this.x; } // foo는 메서드다
    
      //bar에 바인딩 된 함수는 메서드가 아닌 일반 함수다.
      bar: function() { return this.x; }
    };
    
    obj.foo // 1
    obj.bar // 1
    ```
    
    - ES6 사양에서 정의한 메서드는 인스턴스를 생성할 수 없는 non-constructor이다. 따라서 생성자 함수로서 호출할 수 없다.
        
        ```jsx
        new obj.foo(); // is not a function
        ```
        
    - ES6의 메서드는 인스턴스를 생성할 수 없으므로 prototype 프로퍼티가 없고 프로토타입도 생성하지 않는다.<br>
    
[위로](#목차)
 <br>
 
 ## 스코프

- 변수에 접근할 수 있는 범위
- 스코프(유효범위)는 자바스크립트를 포함한 모든 프로그래밍 언어의 기본적이며 중요한 개념
- 함수의 매개변수는 함수 몸체 내부에서만 참조할 수 있고, 함수 몸체 외부에서는 참조할 수 없음<br>
매개변수를 참조할 수 있는 유효범위, 즉 매개변수의 스코프가 함수 몸체 내부로 한정되어 있기 때문
    
- 변수는 코드의 가장 바깥 영역뿐 아니라 코드 블록이나 함수 몸체 내에서도 선언이 가능<br>
- 모든 식별자(변수 이름, 함수 이름, 클래스 이름 등)는 자신이 선언된 위치에 의해 다른 코드가 식별자 자신을 참조할 수 있는 범위가 결정됨 
<br> → 이것이 `스코프` ! 즉,  `스코프` 는 식별자가 유효한 범위를 말함
- 아래의 예제는 어떻게 작동할까?
- <img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b88bc925-8036-4041-8620-565f638e4294/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220627%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220627T041452Z&X-Amz-Expires=86400&X-Amz-Signature=13392a241f8b7df488ceb203cabf216edfdf3dac9c3b661e3d802fb08786af5b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject"></img>
    
    - 코드의 가장 바깥 영역과 foo 함수 내부에 같은 이름을 갖는 x 변수를 선언했고, (1)과 (2)에서 x 변수를 참조함
    - 이때 자바스크립트 엔진은 같은 이름의 두 변수 중에서 어떤 변수를 참조해야 할 것인지 결정해야 하는데, 이를 `식별자 결정` 이라고 함
    - 자바스크립트 엔진은 `스코프` 를 통해 어떤 변수를 참조해야 할 것인지 결정
    - 따라서 `스코프` 란 자바스크립트 엔진이 `식별자를 검색할 때 사용하는 규칙`
    - 자바스크립트 엔진은 코드를 실행할 때 코드의 문맥(context)을 고려함.
    - 코드가 어디서 실행되며 주변에 어떤 코드가 있는지에 따라 위처럼 동일한 코드도 다른 결과가 나옴
    - 위 예제에서 코드의 가장 바깥 영역에 선언된 x 변수는 어디서든 참조할 수 있음
    - 하지만 foo 함수 내부에서 선언된 x 변수는 foo 함수 내부에서만 참조할 수 있고 외부에선 불가능
    - 이때 두 개의 x 변수는 식별자 이름이 동일하지만 자신이 유효한 범위, 즉 스코프가 다른 별개의 변수
    
        
- 만약 스코프 라는 개념이 없다면 같은 이름을 갖는 변수는 충돌을 일으키므로 프로그램 전체에서 하나밖에 사용할 수 없음
- `식별자` 란 변수나 함수의 이름과 같이 어떤 값을 구별하여 식별해 낼 수 있는 고유한 이름<br>
어떤 값을 구별할 수 있어야 하기 때문에 유일 해야하므로 식별자인 변수 이름은 중복될 수 없음<br>
즉, 하나의 값은 `유일한 식별자`에 `연결(name binding)`되어야 함
- 프로그래밍 언어에서는 스코프(유효범위)를 통해 식별자인 변수 이름의 충돌을 방지하여 같은 이름의 변수를 사용할 수 있게 함
- 스코프 내에서 식별자는 유일해야 하지만, 다른 스코프에는 같은 이름의 식별자를 사용할 수 있다.
- 즉, 스코프는 `네임 스페이스` !

<br>

### 스코프의 종류
- 코드는 `전역(global)` 과 `지역(local)` 으로 구분할 수 있음
    
    | 구분 | 설명 | 스코프 | 변수 |
    | --- | --- | --- | --- |
    | 전역 | 코드의 가장 바깥 영역 | 전역 스코프 | 전역 변수 |
    | 지역 | 함수 몸체 내부 | 지역 스코프 | 지역 변수 |
- 이때 변수는 자신이 선언된 위치(전역 또는 지역)에 의해 자신이 유효한 범위인 스코프가 결정됨

### 전역과 전역 스코프

- `전역` : 코드의 가장 바깥 영역
- 전역은 `전역 스코프` 를 만듦
- 전역에 변수를 선언하면 전역 스코프를 갖는 `전역 변수` 가 됨
- 전역 변수는 어디서든지 참조할 수 있음

### 지역과 지역 스코프

- `지역` : 함수 몸체 내부
- 지역은 `지역 스코프` 를 만듦
- 지역에 변수를 선언하면 지역 스코프를 갖는 `지역 변수` 가 됨
- 지역 변수는 자신이 선언된 지역과 하위 지역(중첩 함수)에서만 참조할 수 있음
- 지역 변수는 자신의 지역 스코프와 하위 지역 스코프에서만 유효함
<br>

### 스코프 체인

- 함수는 전역에서도, 함수 몸체 내부에서도 정의할 수 있음
- 함수 몸체 내부에서 함수가 정의된 것을 `함수의 중첩` 이라 함
- 함수 몸체 내부에서 정의한 함수를 `중첩 함수`
- 중첩 함수를 포함하는 함수를 `외부 함수` 라고 함
- 함수는 중첩될 수 있으므로 함수의 지역 스코프도 중첩이 가능함
- 이는 스코프가 `함수의 중첩` 에 의해 `계층적 구조` 를 갖는다는 것을 의미
- 즉, 중첩 함수의 지역 스코프는 중첩 함수를 포함하는 외부 함수의 지역 스코프와 계층적 구조를 갖음
- 이때 외부 함수의 지역 스코프를 중첩 함수의 상위 스코프라 함
    
- 모든 스코프는 `하나의 계층적 구조` 로 연결되며, 모든 지역 스코프의 최상위 스코프 = `전역 스코프`
- 이렇게 스코프가 계층적으로 연결된 것을 `스코프 체인` 이라 함
- 변수를 참조할 때 자바스크립트 엔진은 스코프 체인을 통해 변수를 참조하는 코드의 스코프에서 시작<br>
→ 상위 스코프 방향으로 이동하며 선언된 변수를 검색함<br>
이를 통해 상위 스코프에서 선언한 변수를 하위 스코프에서도 참조할 수 있음
- 스코프 체인은 물리적인 실체로 존재함.<br>
자바스크립트 엔진은 코드(전역 코드와 함수 코드)를 실행하기에 앞서 렉시컬 환경을 실제로 생성함
    - `렉시컬 환경`
        - 코드가 어디서 실행되며 주변에 어떤 코드가 있는지 를 렉시컬 환경이라고 함
        - 즉, 코드의 문맥(context) 은 렉시컬 환경으로 이루어지고, 이를 구현한 것이 실행 컨텍스트
        - 모든 코드는 실행 컨텍스트에서 평가되고 실행됨
        - 스코프 체인은 실행 컨텍스트의 렉시컬 환경을 단방향으로 연결한 것임
        - 전역 렉시컬 환경은 코드가 로드되면 곧바로 생성되고, 
        함수 렉시컬 환경은 함수가 호출되면 생성됨

### 스코프 체인에 의한 변수 검색

- 자바스크립트 엔진은 스코프 체인을 따라 변수를 참조하는 코드의 스코프에서 → 상위 스코프 방향으로 이동하며 선언된 변수를 검색함
- 절대로 하위 스코프로 내려가면서 식별자를 검색할 일은 없음
- 상위 스코프에서 유효한 변수는 하위 스코프에서 자유롭게 참조할 수 있지만, 하위 스코프에서 유효한 변수를 상위 스코프에서 참조할 수 없음

### 스코프 체인에 의한 함수 검색

- 함수 선언문으로 함수를 정의하면 런타임 이전에 함수 객체가 먼저 생성됨<br>
그리고 자바스크립트 엔진은 함수 이름과 동일한 이름의 식별자를 암묵적으로 선언하고 생성된 함수 객체를 할당
    
    - 모든 함수는 함수 이름과 동일한 이름이 식별자에 할당됨
    - (1)에서 foo 함수 호출하면 자바스크립트 엔진은 함수를 호출하기 위해 먼저 함수를 가르키는 식별자 foo 를 검색함
    - 이처럼 함수도 식별자에 할당되기 때문에 스코프를 갖음
    - 사실 함수는 식별자에 함수 객체가 할당된 것 외에는 일반 변수와 다르지 않기 때문에, 스코프를 `식별자를 검색하는 규칙` 이라고 함

### 함수 레벨 스코프

- 지역은 함수 몸체 내부를 말하고 지역은 지역 스코프를 만듦<br>
이는 코드 블록이 아닌 함수에 의해서만 지역 스코프가 생성된다는 것임
- 대부분의 프로그래밍 언어는 함수 몸체만이 아니라 모든 코드 블록(if, for, while, try/catch 등)이<br>
지역 스코프를 만듦 → 이러한 특성을 `블록 레벨 스코프`
- 하지만 `var` 키워드로 선언된 변수는 오로지 `함수의 코드 블록(함수 몸체)` 만을 `지역 스코프` 로 인정<br>
→ 이러한 특성을 `함수 레벨 스코프`<br>

- `함수 레벨 스코프` 란 함수 코드 블록 내에서 선언된 변수는 함수 코드 블록 내에서만 유효하고, 함수 외부에서는 유효하지 않다(참조할 수 없다)는 것
- `var` 키워드로 선언된 변수는 `함수의 코드 블록(함수 몸체)`만을 지역 스코프로 인정함
- `함수 밖`에서 `var` 키워드로 선언된 변수는 코드 블록 내에서 선언되었다 할 지라도 모두 `전역변수`<br>

- 따라서 x 는 전역변수. 이미 선언된 전역 변수 x 가 있으므로 x 변수는 `중복 선언` 됨
- 이는 `의도치 않게 전역 변수의 값이 재할당`되는 부작용이 발생
- `for 문` 에서 선언한 i 는 전역변수. 이미 선언된 전역변수 i 가 있으므로 중복 선언됨
    
    ```jsx
    var i = 10;
    
    for(var i=0; i < 5; i++){
      console.log(i); // 0, 1, 2, 3, 4
    }
    
    console.log(i); // 5
    ```
    
    - 블록 레벨 스코프를 지원하는 프로그래밍 언어에서는 for 문에서 반복을 위해 선언된 변수 i 가 for 문의 코드 블록 내에서만 유효한 지역 변수
    - 하지만 var 키워드로 선언된 변수는 블록 레벨 스코프를 인정하지 않기 때문에 변수 i 는 전역변수
    - 따라서 전역변수 i 는 중복 선언되고 그 결과 의도치 않은 전역 변수의 값이 재할당됨
- `var` 키워드로 선언된 변수는 오로지 `함수의 코드 블록`만을 지역 스코프로 인정하지만, ES6 에서 도입된 `let` , `const` 키워드는 `블록 레벨 스코프` 를 지원함
<br>

### 렉시컬 스코프

- 아래 예제의 실행 결과는 bar 함수의 상위 스코프가 무엇인지에 따라 결정됨
- 두 가지 패턴을 예측할 수 있는데,
    
    > **1. 함수를 어디서 호출했는지에 따라 함수의 상위 스코프를 결정한다.**
    > 
    > - bar 함수의 상위 스코프는 foo 함수의 지역 스코프와 전역 스코프
    > - `동적 스코프`
    > - 함수를 정의하는 시점에는 함수가 어디서 호출될 지 알 수 없음
    > 따라서 함수가 `호출` 되는 시점에 `동적` 으로 상위 스코프를 결정해야 하기 때문에 동적 스코프!
    
    > **2. 함수를 어디서 정의했는지에 따라 함수의 상위 스코프를 결정한다.**
    > 
    > - bar 함수의 상위 스코프는 전역 스코프
    > - `렉시컬 스코프` 또는 `정적 스코프`
    > - 함수 정의가 평가되는 시점에 상위 스코프가 `정적`으로 결정되어 `정적 스코프` 라고 부름
    > - 자바스크립트를 비롯한 대부분의 프로그래밍 언어는 `렉시컬 스코프` 를 따름

- 자바스크립트는 `렉시컬 스코프` 를 따르므로, 함수를 `어디서` 정의 했는지에 따라 상위 스코프를 결정함
- 함수가 호출된 위치는 상위 스코프 결정에 어떠한 영향도 주지 않음.
- 즉, 함수의 상위 스코프는 언제나 `자신이 정의된 스코프`
- 이처럼 함수의 상위 스코프는 함수 정의가 실행될 때 `정적` 으로 결정됨
- 함수 정의(함수 선언문/함수 표현식)가 실행되어 생성된 함수 객체는 이렇게 결정된 상위 스코프를 기억함<br>
함수가 호출될 때마다 함수의 상위 스코프를 참조할 필요가 있기 때문

- 위의 예제의 bar 함수는 전역에서 정의된 함수
- 함수 선언문으로 정의된 bar 함수는 전역 코드가 실행되기 전에 먼저 평가되어 함수 객체를 생성함
- 이때 생성된 bar 함수 객체는 자신이 정의된 스코프, 즉 전역 스코프를 기억함
- 그리고 bar 함수가 호출되면 호출된 곳이 어디인지 관계없이 언제나 자신이 기억하고 있는 전역 스코프를 상위 스코프로 사용함
- 따라서 위의 예제를 실행하면 아래와 같이 전역 변수 x 의 값 1을 두 번 출력한다. <br>

[위로](#목차)


## 디스트럭처링 할당
- 구조 분해 할당은 구조화된 배열과 같은 이터러블 또는 객체를 비구조화 하여 1개 이상의 변수에 개별적으로 할당하는 것
- 배열과 같은 이터러블 또는 객체 리터럴에서 필요한 값만 추출하여 변수에 할당할 때 유용함

### 배열 디스트럭처링 할당
- ES6의 배열 구조 분해 할당은 배열의 각 요소를 배열로부터 추출하여 1개 이상의 변수에 할당
- 이때 배열 구조 분해 할당의 대상(할당문의 우변)은 이터러블이어야 하며, 배열의 순서대로 할당됨

```js
const arr = [1, 2, 3];
const [one, two, three] = arr; 

console.log(one, two, three); // 1 2 3
```

- 배열 구조분해 할당을 위해서는 할당 연산자 왼쪽에 값을 할당받을 변수를 선언해야 함
- 이때 변수를 배열 리터럴 형태로 선언함
- 우변에 이터러블을 할당하지 않으면 에러가 발생함

```js
const [x, y]; 
// SyntaxError: Missing initializer in destructuring declaration

const [a, b] = {}; 
// TypeError: {} is not iterable
```

- 배열 구조분해 할당의 기준은 배열의 인덱스. 즉, 순서대로 할당됨
- 이때 변수의 개수와 이터러블의 요소 개수가 반드시 일치할 필요는 없음

```js
const [a, b] = [1];
console.log(a,b) // 1 undefined

const [c, ,e] = [1, 2 ,3];
console.log(c,e); // 1 3
```

- 배열 구조분해 할당을 위한 변수에 기본값을 설정할 수 있음
```js
const [a, b, c = 3] = [1, 2];
console.log(a,b,c) // 1 2 3

// 기본값보다 할당된 값이 우선한다.
const [e, f = 10, g = 3] = [1, 2];
console.log(e,f,g) // 1 2 3
```
- 배열 구조분해 할당을 위한 변수에 Rest 파라미터와 유사하게 Rest 요소 `...` 를 사용할 수 있음
- Rest 요소는 Rest 파라미터와 마찬가지로 반드시 마지막에 위치해야 함
```js
//Rest 요소
const [x, ...y] = [1, 2, 3];
console.log(x,y) // 1 [ 2, 3 ]
```

<br>

### 객체 디스트럭처링 할당
- ES6의 객체 구조분해 할당은 객체의 각 프로퍼티를 객체로부터 추출하여 1개 이상의 변수에 할당함
- 이때 객체 구조분해 할당의 대상(우변)은 객체이어야 하며, 할당 기준은 `프로퍼티 키` 
- 즉, 순서는 의미가 없고 선언된 변수 이름과 프로퍼티 키가 일치하면 할당됨
```js
const minsu = {firstName: '야끼니꾸', lastName: '민수'}
const {lastName, firstName} = minsu;

console.log(firstName, lastName); // '야끼니꾸' '민수'
```

- 배열 구조분해 할당과 마찬가지로 객체 구조분해 할당을 위해서는 할당 연산자 왼쪽에 프로퍼티 값을 할당받을 변수를 선언해야 함
- 이때 변수를 객체 리터럴 형태로 선언함
- 우변에 객체 또는 객체로 평가될 수 있는 표현식을 할당하지 않으면 에러 발생
```js
const {lastName, firstName} = user;
// 위와 아래는 동치
// 프로퍼티 축약 표현을 통해 선언한 것 
const {lastName: lastName, firstName: firstName} = user;
```
- 객체의 프로퍼티 키와 다른 변수 이름으로 프로퍼티 값을 할당받으려면 다음과 같이 변수를 선언함
```js
const user = {firstName: '재혁', lastName:'임'};
const {lastName: ln, firstName: fn} = user;

console.log(ln, fn); // '임' '재혁'
```

- 객체 구조분해 할당을 위한 변수에 기본값을 설정할 수 있음
```js
const {firstName = 'boyoon',lastName} = { lastName:'kim'};
console.log(firstName, lastName); // 'boyoon' 'kim'

const {firstName:fn ='boyoon', lastName:ln}={lastName:'kim'};
console.log(fn, ln) // 'boyoon' 'kim'
```
- 객체 구조분해 할당은 객체에서 프로퍼티 키로 필요한 프로퍼티 값만 추출하여 변수에 할당하고 싶을 때 유용함
```js
const str = 'MinsuMansu';
const {length} = str
console.log(length); // 10

const todo = {id:1, content:'딥다이브 개념정리', completed:'true'};
// todo 객체로부터 id 프로퍼티만 추출함
const { id } = todo;
console.log(id); // 1
```


- 객체 구조분해 할당은 객체를 인수로 전달받는 함수의 매개변수에도 사용할 수 있음
```js
function printTodo(todo){
  console.log(`할일 ${todo.content}는 ${todo.completed ? '완료' : '비완료'} 상태 입니다.`);
}

printTodo({id:1, content:'딥다이브 개념정리', completed:'true'})
// '할일 딥다이브 개념정리는 완료 상태 입니다.'
```

- 위 예제에서 객체를 인수로 전달받는 매개변수 todo에 객체 구조분해 할당을 사용하면 좀 더 간단하고 가독성이 좋아짐

```js
function printTodo({content, completed}){
  console.log(`할일 ${content}는 ${completed ? '완료' : '비완료'} 상태 입니다.`);
}

printTodo({id:1, content:'딥다이브 개념정리', completed:'true'})
// '할일 딥다이브 개념정리는 완료 상태 입니다.'
```
- 배열의 요소가 객체인 경우 배열 구조분해 할당과 객체 구조분해 할당을 혼용할 수 있음
```js
const todos = [
  {id: 1, content: '딥다이브', completed: true},
  {id: 2, content: '면접준비', completed: false},
  {id: 3, content: '프로젝트', completed: false},
];

const [, {id, content}] = todos;
console.log(id) // 2 
console.log(content) // '면접준비'
console.log(id, content) // 2 '면접준비'
```

- 중첩 객체의 경우는 다음과 같이 사용함
```js
const user = {
  name: '민수',
  address: {
    zipCode: '33333',
    city: 'Tokyo'
  }
};

// address 프로퍼티 키로 객체를 추출하고 
// 이 객체의 city 프로퍼티 키로 값을 추출함
const { address: { city } } = user;
console.log(city); // 'Tokyo'
```

- 객체 구조분해 할당을 위한 변수에 Rest 파라미터나 Rest 요소와 유사하게 `Rest 프로퍼티 ...` 을 사용할 수 있음
- Rest 프로퍼티는 Rest 파라미터나 Rest 요소와 마찬가지로 반드시 마지막에 위치 <br>
```js
const { x, ...rest } = { x: 1, y: 2, z: 3};
console.log(x, rest) // 1 { y: 2, z: 3 }
```

[위로](#목차) 

## 브라우저의 렌더링 과정
- 파싱? 
  - 프로그래밍 언어의 문법에 맞게 작성된 텍스트 문서를 읽어 들여 실행하기 위해 텍스트 문서의 문자열을 토큰으로 분해하고, 토큰에 문법적 의미와 구조를 반영하여 트리 구조의 자료구조인 파스 트리를 생성하는 일련의 과정을 말함
- 렌더링?
  - HTMl, CSS, 자바스크립트로 작성된 문서를 파싱하여 브라우저에 시각적으로 출력하는 것을 말함

- 브라우저는 다음과 같은 과정을 거쳐 렌더링을 수행함
  1. 브라우저는 HTML, CSS, 자바스크립트, 이미지, 폰트 파일 등 렌더링에 필요한 리소스를 요청하고 서버로부터 응답을 받음
  2. 브라우저의 렌더링 엔진은 서버러부터 응답된 HTML과 CSS를 파싱하여 DOM과 CSSOM을 생성하고 이들을 결합하여 렌터 트리를 생성함
  3. 브라우저의 자바스크립트 엔진은 서버로부터 응답된 자바스크립트를 파싱하여 AST(Abstract Syntax Tree)를 생성하고 바이트코드로 변환하여 실행함. 이때 자바스크립트는 DOM API 를 통해 DOM이나 CSSOM을 변경할 수 있음. 변경된 DOM과 CSSOM은 다시 렌더 트리로 결함됨 
  4. 렌더 트리를 기반으로 HTML 요소의 레이아웃(위치와 크기)을 계산하고 브라우저 화면에 HTML 요소를 페인팅 함 
<br>

### 요청과 응답
- 브라우저의 핵심 기능은 필요한 리소스를 서버에 요청하고, 서버로부터 응답을 받아 브라우저에 시각적으로 렌더링 하는 것 
- 즉, 렌더링에 필요한 리소스는 모두 서버에 존재하므로 필요한 리소스를 서버에 요청하고 서버가 응답한 리소스를 파싱하여 렌더링하는 것
- 서버에 요청을 전송하기 위해 브라우저는 주소창을 제공함
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F4jfhy%2Fbtrvbhya9KK%2FMSygerMcKAdZbWsJP33KzK%2Fimg.png">

- 서버에 요청을 하기 위해서는 브라우저 주소창에 URL을 입력하고 엔터키를 누름 
- URL의 호스트 이름이 DNS를 통해 IP 주소로 변환되고 이 IP 주소를 갖는 서버에게 요청을 전송함
- 요청과 응답은 개발자도구 Network 패널에서 확인 가능
- 브라우저의 렌더링 엔진이 HTML을 파싱하는 도중에 외부 리소스를 로드하는 태그, 즉 CSS 파일 로드하는 link 태그, img 태그, script 태그 등 만나면 HTML의 파싱을 일시 중단하고 해당 리소스 파일로 서버를 요청하기 때문

<br>

### HTML 파싱과 DOM 생성
- 브라우저의 요청에 의해 서버가 응답한 HTML 문서는 문자열로 이루어진 순수한 텍스트
- 이러한 HTML 문서를 브라우저에 시각적인 픽셀로 렌더링 하려면 브라우저가 이해할 수 있는 자료구조(객체)로 변환하여 메모리에 저장해야 함
- 브라우저의 렌더링 엔진은 응답받은 HTML 문서를 파싱하여 브라우저가 이해할 수 있는 자료구조인 DOM(Document Object Model)을 생성함
- `DOM` 은 `HTML 문서를 파싱한 결과물`

<br>

### CSS 파싱과 CSSOM 생성
- 렌더링 엔진은 HTML 을 처음부터 한 줄씩 순차적으로 파싱하며 DOM 을 생성해 나감
- 도중에 link 태그나 style 태그를 만나면 DOM 생성을 일시 중단함
- link 태그의 href 어트리뷰트에 지정된 CSS 파일을 서버에 요청하여 로드한 CSS 파일이나, 
- style 태그 내의 CSS를 HTML과 동일한 파싱 과정을 거치며 해석하여 CSSOM 을 생성함
- 이후 CSS 파싱을 완료하면 HTML 파싱이 중단된 지점부터 다시 HTML 파싱하기 시작하여 DOM 생성을 재개함
<br>


### 렌더 트리 생성
- 렌더링 엔진은 서버로부터 응답된 `HTML` 과 `CSS` 를 파싱하여 각각 `DOM` 과 `CSSOM` 를 생성함
- DOM 과 CSSOM 은 렌더링을 위해 `렌더 트리`로 결합됨
- 렌더 트리는 렌더링을 위한 트리 구조의 자료구조 
- 따라서 브라우저 화면에 렌더링되지 않는 노드(meta, script 태그 등)와 CSS에 의해 비표시되는 노드들은 포함하지 않음
- 즉, 렌더 트리는 브라우저 화면에 렌더링되는 노드만으로 구성됨
- 이후 완성된 렌더 트리는 각 HTML 요소의 레이아웃(위치와 크기)을 계산하는 데 사용되며 브라우저 화면에 픽셀을 렌더링하는 페인팅 처리에 입력됨
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcmYdP4%2Fbtru9Po3G9K%2FddHcmCNkMMaT7daDaRKDDK%2Fimg.png">

- 브라우저의 렌더링 과정은 반복해서 실행될 수 있음 
- 리렌더링은 성능에 악영향을 주는 작업이므로 가급적 빈번하게 발생하지 않도록 주의해야 함

<br>

### 자바스크립트 파싱과 실행
- HTML 문서를 파싱한 결과물로서 생성된 DOM은 HTML 문서의 구조와 정보뿐만 아니라 HTML 요소와 스타일 등을 변경할 수 있는 프로그래밍 인터페이스로서 DOM API를 제공함
- 즉, 자바스크립트 코드에서 DOM API 를 사용하면 이미 생성된 DOM 을 동적으로 조작할 수 있음
- 렌더링 엔진은 HTML 을 한 줄씩 순차적으로 파싱하다 script 태그를 만나면 DOM 생성을 일시 중지함
- 그리고 script 태그 내의 자바스크립트 코드 등을 파싱하기 위해 자바스크립트 엔진에 제어권을 넘김
- 이후 자바스크립트 파싱과 실행이 종료되면 DOM 생성을 재개함
- 자바스크립트 파싱과 실행은 자바스크립트 엔진이 처리함
- 렌더링 엔진으로부터 제어권을 넘겨받은 자바스크립트 엔진이 자바스크립트 코드를 파싱하는데,
- 자바스크립트 엔진은 자바스크립트를 해석하여 AST(Abstruct Syntax Tree 추상적 구문 트리)를 생성하고, 이를 기반으로 인터프리터가 실행할 수 있는 중간 코드인 바이트코드를 생성하여 실행함

<br>

### 리플로우와 리페인트
- 자바스크립트 코드에서 DOM 이나 CSSOM 을 변경하는 DOM API가 사용된 경우 DOM 이나 CSSOM이 변경됨
- 이때 변경된 DOM과 CSSOM은 다시 렌더 트리로 결합되고 변경된 렌더 트리를 기반으로 레이아웃과 페인트 과정을 거쳐 브라우저의 화면에 다시 렌더링 함
- 이를 `리플로우`, `리페인트` 라고 함
- 리플로우는 레이아웃을 다시 계산하는 것을 말하는 것으로, <br>
노드 추가/삭제, 요소 크기/위치 변경 등 레이아웃에 영향을 주는 변경이 발생한 경우에 한하여 실행됨
- 리페인트는 재결합된 렌터 트리를 기반으로 다시 페인트를 하는 것
- 기존 요소에 변경 사항이 생겼다고 항상 리플로우-리페인트가 일어나는 것은 아님
- 레이아웃에 영향이 미치지 않는 단순 색상 변경 같은 사항은 리플로우 수행 없이 리페인트만 수행하게 됨
- 하지만 리플로우가 일어나면 반드시 리페인트가 수행됨
 
- 리플로우(Reflow)가 일어나는 대표적인 속성들
  - position
  - width, height, margin, padding
  - border, border-width
  - font-size, font-weight 
  - line-height, text-align, overflow

- 리페인트(Repaint)만 일어나는 대표적인 속성들
  - background
  - color, text-decoration 
  - border-style, border-radius

<br>

### 자바스크립트 파싱에 의한 HTML 파싱 중단
- 렌더링 엔진과 자바스크립트 엔진은 직렬적으로 파싱을 수행함
- 즉, HTML 문서에서 위에서 아래 방향으로 순차적으로 HTML, CSS, JS를 파싱하고 실행함
- 이때 script 태그의 위치에 따라 HTML 파싱이 블로킹 되어 DOM 생성이 지연될 수 있으므로, script 태그의 위치는 중요한 의미를 갖음
- 만약 자바스크립트 코드가 DOM을 변경하는 DOM API를 사용할 때 DOM 생성이 완료되지 않은 상태라면 문제가 발생할 수 있음
- 또한 자바스크립트 로딩/파싱/실행으로 인해 HTML 요소들의 렌더링에 지장받아 페이지 로딩 시간이 늘어날 수 있음
- 이를 해결하기 위해서 body 요소의 가장 아래에 자바스크립트를 위치시키거나, async/defer 어트리뷰트를 이용하는 방법이 있음

<br>

### script 태그의 async/defer 어트리뷰트
- 자바스크립트 파싱에 의한 DOM 생성이 중단되는 문제를 근본적으로 해결하기 위해 HTML5부터 script 태그에 async와 defer 어트리뷰트가 추가되었음
- async/defer 어트리뷰트는 src 어트리뷰트를 통해 외부 자바스크립트 파일을 로드하는 경우에만 사용이 가능함
```js
<script async src="extern.js"></script>
<script defer src="extern.js"></script>
```
- async/defer 어트리뷰트를 사용하면 HTML 파싱과 외부 자바스크립트 파일의 로드가 비동기적으로 동시에 진행됨
- 하지만 자바스크립트의 실행 시점에 차이가 존재

<br>

### async 어트리뷰트
- HTML 파싱과 외부 자바스크립트 파일의 로드가 비동기적으로 동시에 진행됨
- 단, 자바스크립트 파싱과 실행은 자바스크립트 파일의 로드가 완료된 직후 진행되며 이때 HTML 파싱이 중단됨
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsQd8c%2FbtrvhMKUIDi%2F8z4acSXPTfhDjoAW7QpagK%2Fimg.png">

- 여러개의 script 태그에 async 를 지정하면 script 태그의 순서와는 상관없이 로드가 완료된 자바스크립트 부터 먼저 실행되므로 순서가 보장되지 않음

<br>

### defer 어트리뷰트
- async 와 마찬가지로 HTML 파싱과 외부 자바스크립트 파일의 로드가 비동기적으로 동시에 진행됨
- 단, 자바스크립트의 파싱과 실행은 HTML 파싱이 완료된 직후
- 즉, DOM 생성이 완료된 직후 진행됨
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Ft0E6H%2FbtrvaJPEvX7%2FjIW8nHYtZnfo9KndoMKZkK%2Fimg.png">

- 따라서 DOM 생성이 완료된 이후 실행되어야 할 자바스크립트에 유용함
<br>

[위로](#목차)


## DOM
- DOM(Document Object Model) 은 HTML 문서의 계층적 구조와 정보를 표현하며 이를 제어할 수 있는 API, 즉 프로퍼티와 메서드를 제공하는 트리 자료구조 
<br>

### HTML 요소와 노드 객체 
- HTML 요소는 HTML 문서를 구성하는 개별적인 요소를 의미
- HTML 요소는 렌더링 엔진에 의해 파싱되어 DOM 을 구성하는 요소 노드 객체로 변환됨
- 이때 HTML 요소의 어트리뷰트는 어트리뷰트 노드로, HTML 요소의 텍스트 콘텐츠는 텍스트 노드로 변환됨
- HTML 문서는 HTML 요소들의 집합으로 이뤄지며, HTML 요소는 중첩 관계를 갖음
- 즉, HTML 요소의 콘텐츠 영역(시작 태그와 종료 태그 사이)에는 텍스트뿐만 아니라 다른 HTML 요소도 포함할 수 있음
- 이때 HTML 요소 간에는 중첩 관계에 의해 계층적인 부자 관계가 형성됨
- 이러한 HTML 요소 간의 부자 관계를 반영하여 HTML 문서의 구성요소인 HTML 요소를 객체화한 모든 노드 객체들을 트리 자료 구조로 구성함

<br>

### 트리 자료구조 
- 노드들의 계층 구조로 이루어짐
- 즉, 트리 자료구조는 부모 노드와 자식 노드로 구성되어 노드 간의 계층적 구조(부자, 형제 관계)를 표현하는 비선형 자료구조 를 말함
- 트리 자료구조는 하나의 최상위 노드에서 시작함
- 최상위 노드는 부모 노드가 없으며, 루트 노드라 함
- 루트 노드는 0개 이상의 자식 노드를 갖음 
- 자식 노드가 없는 노드를 리프 노드 라고 함
- 노드 객체들로 구성된 트리 자료구조를 DOM 이라 함
- 노드 객체의 트리로 구조화되어 있기 때문에 DOM 을 DOM 트리라고 부름

### 노드 객체의 타입
- 렌더링 엔진은 HTML 문서를 파싱하여 다음과 같이 DOM을 생성함
  ```html
  <!DOCTYPE html>
  <html>  
    <head>
      <meta charset="UTF-8">
      <link rel="stylesheet" href="style.css">
    </head>
    <body>
      <ul>
        <li id="apple">Apple</li>
        <li id="banana">Banana</li>
        <li id="orange">Orange</li>
      </ul>
      <script src="app.js"></script>
    </body>
  </html>
  ```
  
  <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbPAbSi%2FbtrAVsA1ACk%2F7mEGOEkGVyjXitUwriik11%2Fimg.png">

- 이처럼 DOM 은 노드 객체의 계층적인 구조로 구성됨
- 노드 객체는 총 12개의 종류(노드 타입)가 있음
- 그 중 4개가 중요함! 

#### `문서 노드`
- 문서 노드는 DOM 트리의 최상위에 존재하는 루트 노드로서 document 객체를 가리킴
- document 객체는 브라우저가 렌더링한 HTML 문서 전체를 가리키는 객체로서 전역 객체 window의 document 프로퍼티에 바인딩 되어있음
- 따라서 문서 노드는 window.document 또는 document 로 참조할 수 있음
- 브라우저 환경의 모든 자바스크립트 코드는 script 태그에 의해 분리되어 있어도 하나의 전역 객체 window 를 공유함
- 따라서 모든 자바스크립트 코드는 전역 객체 window의 document 프로퍼티에 바인딩 되어 있는 하나의 document 객체를 바라봄
- 즉, HTML 문서당 document 객체는 유일함
- 문서노드, 즉 document 객체는 DOM 트리의 루트 노드이므로 DOM 트리의 노드들에 접근하기 위한 진입점 역할을 담당
- 즉, 요소, 어트리뷰트, 텍스트 노드에 접근하려면 문서 노드를 통해야 함

#### `요소 노드`
- 요소 노드는 HTML 요소를 가리키는 객체
- HTML 요소 간의 중첩에 의해 부자 관계를 가지며, 이를 통해 정보를 구조화 함
- 따라서 요소 노드는 문서의 구조를 표현함

#### `어트리뷰트 노드`
- 어트리뷰트 노드는 HTML 요소의 어트리뷰트를 가리키는 객체
- 어트리뷰트가 지정된 HTML 요소의 요소 노드와 연결되어 있음
- 어트리뷰트 노드는 부모 노드가 없고 요소 노드에만 연결되어 있음
- 어트리뷰트를 참조하거나 변경하려면 먼저 요소 노드에 접근해야 함

#### `텍스트 노드`
- 텍스트 노드는 HTML 요소의 텍스트를 가리키는 객체
- 요소 노드가 문서의 구조를 표현한다면, 텍스트 노드는 문서의 정보를 표현함
- 텍스트 노드는 DOM 트리의 최종단
- 텍스트 노드에 접근하려면 먼저 부모 노드인 요소 노드에 접근해야 함

<br>

### 노드 객체의 상속 구조
- DOM 을 구성하는 노드 객체는 자신의 구조와 정보를 제어할 수 있는 DOM API 를 사용할 수 있음
- DOM 을 구성하는 노드 객체는 ECMAScript 사양에 정의된 표준 빌트인 객체가 아닌, 브라우저 환경에서 추가적으로 제공하는 호스트 객체임
- 하지만 노드 객체도 자바스크립트 객체이므로 프로토타입에 의한 상속 구조를 갖음
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcDX134%2FbtrAYmthuJ7%2FGlcerFsrqKiqY62CvNFbpK%2Fimg.png">
- 모든 노드 객체는 Object, EventTarget, Node 인터페이스를 상속받음
- input 요소 노드 객체의 특성
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcetzMz%2FbtrAWA6BMpc%2FmEfMLikTstxrjQQkLvR2BK%2Fimg.png">

- 노드 객체의 상속 구조는 개발자 도구 Elements 패널 우측의 Properties 패널에서 확인 가능
- DOM 은 HTML 문서의 계층적 구조와 정보를 표현하는 것은 물론 노드 객체의 종류, 즉 노드 타입에 따라 필요한 기능을 프로퍼티와 메서드의 집합인 DOM API 로 제공함
- 이 DOM API 를 통해 HTML 의 구조나 내용 또는 스타일 등을 동적으로 조작할 수 있음
<br>

[위로](#목차)

## 프로미스

- 자바스크립트는 비동기 처리를 위한 하나의 패턴으로 콜백 함수를 사용
- 하지만 전통적인 콜백 패턴은 콜백 헬로 인해 가독성이 나쁘고 비동기 처리 중 발생한 에러 처리가 곤란
- 또한 여러개의 비동기 처리를 한번에 처리하는 데에도 한계가 있음
- ES6에서는 비동기 처리를 위한 또 다른 패턴으로 Promise 를 도입
- Promise 는 전통적인 콜백 패턴이 가진 단점을 보완하며 비동기 처리 시점을 명확하게 표현할 수 있다는 장점 

<br>

### 비동기 처리를 위한 콜백 패턴의 단점
#### `콜백 헬` 
- 예제) GET 요청을 위한 함수
  ```js
  const get = url => {
    const xhr = new XMLHttpRequest();
    xhr.open('GET', url);
    xhr.send();

    xhr.onload = () => {
      if (xhr.status === 200){
        // 서버의 응답을 콘솔에 출력함
        console.log(JSON.parse(xhr.response));
      } else {
        console.error(`${xhr.status} ${xhr.statusText}`);
      }
    };
  };

  // id가 1인 post를 취득
  get('https://jsonplaceholder.typicode.com/posts/1');
  ```
- 위 예제의 get 함수는 서버의 응답 결과를 콘솔에 출력함
- get 함수가 서버의 응답 결과를 반환하게 하려면 어떻게 해야 할까?
- get 함수는 비동기 함수임
- `비동기 함수` 란 함수 내부에 비동기로 동작하는 코드를 포함한 함수임
- 비동기 함수를 호출하면 함수 내부의 비동기로 동작하는 코드가 완료되지 않았다 해도 기다리지 않고 즉시 종료됨
- 즉, 비동기 함수 내부의 비동기로 동작하는 코드는 비동기 함수가 종료된 이후에 완료됨
- 따라서 비동기 함수 내부의 비동기로 동작하는 코드에서 처리 결과를 외부로 반환하거나 상위 스코프의 변수에 할당하면 기대한 대로 동작하지 않음

- 예제) 비동기 함수인 setTimeout 함수
  ```js
  let g = 0;

  // 비동기 함수인 setTimeout 함수는 콜백 함수의 처리 결과를 
  // 외부로 반환하거나 상위 스코프의 변수에 할당하지 못함
 
  setTimeout(() => { g = 100; }, 0);
  console.log(g); // 0
  ```

  - setTimeout 함수가 비동기 함수인 이유는 콜백 함수의 호출이 비동기로 작동하기 때문
  - setTimeout 함수의 콜백 함수는 setTimeout 함수가 종료된 이후에 호출됨
  - setTimeout 함수의 콜백 함수에 상위 스코프의 변수에 값을 할당하면, <br>
  setTimeout 함수는 생성된 타이머를 식별할 수 있는 고유한 타이머 id를 반환하므로 콜백 함수에서 값을 반환하는 것은 무의미함

<br>

- 이처럼 비동기 함수는 비동기 처리 결과를 외부에 반환할 수 없고, 상위 스코프의 변수에 할당할 수도 없음
- 따라서 비동기 함수의 처리 결과(서버의 응답 등)에 대한 후속 처리는 비동기 함수 내부에서 수행해야 함
- 이때 비동기 함수를 범용적으로 사용하기 위해 비동기 함수에 비동기 처리 결과에 대한 후속 처리를 수행하는 콜백 함수를 전달하는 것이 일반적
- 필요에 따라 비동기 처리가 성공하면 호출될 콜백 함수와 실패하면 호출될 콜백 함수를 전달할 수 있음

<br>

```js
// GET 요청을 위한 비동기 함수
const get = (url, callback) => {
  const xhr = new XMLHttpRequest();
  xhr.open('GET', url);
  xhr.send();

  xhr.onload = () => {
    if (xhr.status === 200){
      // 서버의 응답을 콜백 함수에 인수로 전달하면서 호출하여 응답에 대한 후속 처리를 함
      callback(JSON.parse(xhr.response));
    } else {
      console.error(`${xhr.status} ${xhr.statusText}`);
    }
  };
};

const url = 'https://jsonplaceholder.typicode.com';

// id가 1인 post의 userId를 취득
get(`${url}/posts/1`, ({ userId }) => {
  console.log(userId); // 1
  // post의 userId를 사용하여 user 정보 취득
  get(`${url}/users/${userId}`, userInfo => {
    console.log(userInfo);
  });
});
```

- 위 예제를 보면 GET 요청을 통해 서버로부터 응답을 취득하고, 이 데이터를 사용하여 또다시 GET 요청을 함
  ```js
  get('/step1', a => {
    get(`/step2/${a}`, b => {
      get(`/step3/${b}`, c => {
        get(`/step4/${c}`, d => {
          console.log(d);
        });
      });
    });
  });
  ```
- 이처럼 콜백 함수를 통해 비동기 처리 결과에 대한 후속 처리를 수행하는 비동기 함수가, 비동기 처리 결과를 가지고 또다시 비동기 함수를 호출해야 한다면 콜백 함수 호출이 중첩되어 복잡도가 높아지는 현상이 발생하는데
- 이를 `콜백 헬` 이라고 함
- 콜백 헬은 가독성을 나쁘게 하며 실수를 유발하는 원인이 됨

<br>

### 에러 처리의 한계
- 비동기 처리를 위한 콜백 패턴의 문제점 중 가장 심각한 것은 에러 처리가 곤란하다는 것

  ```js
  try {
    setTimeout(() => { throw new Error('Error!'); }, 1000);
  } catch (e) {
    // 에러를 캐치하지 못함
    console.error('캐치한 에러', e);
  }
  ```

  <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb0vpcX%2Fbtrdqga8Eeb%2FOHVaVt3lye5RFNZdflpKxk%2Fimg.png">

- 비동기 함수인 setTimeout 이 호출되면 setTimeout 함수의 실행 컨텍스트가 생성되어 콜 스택에 푸쉬되어 실행됨
- setTimeout 은 비동기 함수이므로 콜백 함수가 호출되는 것을 기다리지 않고 즉시 종료되어 콜 스택에서 제거됨
- 이후 타이머가 만료되면 setTimeout 함수의 콜백 함수는 태스크 큐로 푸시되고 콜 스택이 비어졌을 때 이벤트 루프에 의해 콜 스택으로 푸시되어 실행됨
- setTimeout 함수의 콜백 함수가 실행될 때는 이미 setTimeout 함수는 콜 스택에서 제거가 된 상태임
- 이것은 setTimeout 함수의 콜백 함수를 호출한 것이 setTimeout 함수가 아니라는 것을 의미함 
- 에러는 호출자(caller) 방향으로 전파됨
- 즉, 콜 스택의 아래 방향으로 전파됨
- 위의 예제는 setTimeout 함수의 콜백 함수를 호출한 것이 setTimeout 이 아니기 때문에 setTimeout 함수의 콜백 함수가 발생시키는 에러는 catch 블록에서 캐치되지 않음

<br>

- 즉, 비동기 처리를 위한 콜백 패턴은 `콜백 헬` 이나 `에러 처리` 가 곤란하다는 문제점을 가짐
- 이를 극복하기 위해 `ES6` 에서 `프로미스` 가 도입됨

<br>

### 프로미스의 생성
- Promise 생성자 함수를 `new` 연산자와 함께 호출하면 프로미스(Promise 객체)를 생성함
- ES6 에서 도입된 Promise 는 ECMAScript 사양에 정의된 표준 빌트인 객체
- Promise 생성자 함수는 비동기 처리를 수행할 콜백 함수를 인수로 전달받는데 이 콜백 함수는 resolve 와 reject 함수를 인수로 전달 받음

  ```js
  // 프로미스 생성
  const promise = new Promise((resolve, reject) => {
    // Promise 함수의 콜백 함수 내부에서 비동기 처리를 수행함
    if(/* 비동기 처리 성공*/){
      resolve('result');
    } else { /* 실패 */
      reject('failure reason');
    }
  })
  ```

- Promise 생성자 함수가 인수로 전달받은 콜백 함수 내부에서 비동기 처리를 수행함 
- 이때 비동기 처리가 성공하면 콜백 함수의 인수로 전달받은 resolve 함수, 실패하면 reject 함수를 호출

  ```js
  // GET 요청을 위한 비동기 함수
  const promiseGet = url => {
    return new Promise((resolve, reject) => {
      const xhr = new XMLHttpRequest();   
      xhr.open('GET', url);
      xhr.send();

      xhr.onload = () => {
        if (xhr.status === 200){
          // 성공하면 resolve 함수 호출
          resolve(JSON.parse(xhr.response));
        } else {
          // 에러 처리를 위해 reject 함수 호출
          reject(new Error(xhr.status));
        }
      };
    });
  };

  // promiseGet 함수는 프로미스를 반환
  promiseGet('https://jsonplaceholder.typicode.com/posts/1');
  ```
- 비동기 함수인 promiseGet 은 함수 내부에서 프로미스를 생성하고 반환
- 비동기 처리는 Promise 생성자 함수가 인수로 전달받은 콜백 함수 내부에서 수행
- 성공하면 비동기 처리 결과를 resolve 함수에 인수로 전달하며 호출, 실패하면 에러를 reject 함수에 인수로 전달

- 프로미스는 다음과 같이 현재 비동기 처리가 어떻게 진행되고 있는지 나타내는 상태 정보를 갖음 
<img src="https://velog.velcdn.com/images%2Fniyu%2Fpost%2F94082c0d-b5f2-41de-b1a8-dde17e47e0b4%2Fimage.png">

- 생성된 직후의 프로미스는 기본적으로 pending 상태
- 비동기 처리 성공: resolve 함수 호출해 프로미스를 fullfilled 상태로 변경
- 비동기 처리 실패: reject 함수 호출해 프로미스를 rejected 상태로 변경
- 이처럼 프로미스의 상태는 resolve 또는 reject 함수 호출하는 것으로 결정됨
- 비동기 처리 성공하면 pending -> fulfilled 로 변화하고, 비동기 처리 결과인 1을 값으로 가짐
  <img src="https://velog.velcdn.com/images%2Fniyu%2Fpost%2F58a9919b-b31f-4e69-aecd-ac48c5abb92e%2Fimage.png">

- 비동기 처리 실패하면 pending -> rejected 로 변화하고, 비동기 처리 결과인 Error 객체를 값으로 가짐 
  <img src="https://velog.velcdn.com/images%2Fniyu%2Fpost%2Fb2758d9b-2068-4db3-ac60-fb394c60fcc4%2Fimage.png">


- 즉, 프로미스는 비동기 처리 상태와 처리 결과를 관리하는 객체!

<br>

### 프로미스의 후속 처리 메서드
- 프로미스의 비동기 처리 상태가 변화하면 이에 따른 후속 처리를 해야 함
- 이를 위해 프로미스는 후속 메서드 `then`, `catch`, `finally` 를 제공함
- 프로미스의 비동기 처리 상태가 변화하면 후속 처리 메서드에 인수로 전달한 콜백 함수가 선택적으로 호출됨 
- 이때 후속 처리 메서드의 콜백 함수에 프로미스 처리 결과가 인수로 전달됨
- 모든 후속 처리 메서드는 프로미스를 반환하며, 비동기로 동작됨

<br>

#### `Promise.prototype.then`
- then 메서드는 두 개의 콜백 함수를 인수로 전달 받음
  ```js
  // fulfilled 
  new Promise(resolve => resolve('fulfilled'))
    .then(v => console.log(v), e => console.log(e)); // fulfilled

  // rejected
  new Promise((_, reject) => reject(new Error('rejected')))
    .then(v => console.log(v), e => console.log(e)); // Error: rejected
  ``` 
- 첫 번째 콜백 함수는 `비동기 성공 처리 콜백 함수`<br>
프로미스가 fulfilled 상태(resolve 함수가 호출된 상태)가 되면 호출됨. 이때 콜백 함수는 프로미스의 비동기 처리 결과를 인수로 전달 받음
- 두 번째 콜백 함수는 `비동기 실패 처리 콜백 함수`<br> 프로미스가 rejected 상태가 되면 호출됨. 이때 콜백 함수는 프로미스의 에러를 인수로 전달 받음


- then 메서드는 언제나 프로미스를 반환함
- 만약 then 메서드의 콜백 함수가 프로미스를 반환하면 그 프로미스 그대로 반환하고, 
- 콜백 함수가 프로미스가 아닌 값을 반환하면 그 값을 암묵적으로 resolve 또는 reject 하여 프로미스를 생성해 반환함

<br>

#### `Promise.prototype.catch`
- catch 메서드는 한 개의 콜백 함수를 인수로 전달 받음
- catch 메서드의 콜백 함수는 프로미스가 `rejected` 상태인 경우만 호출됨
  ```js
  // rejected
  new Promise((_, reject) => reject(new Error('rejected')))
    .catch(e => console.log(e)); // Error: 'rejected'
  ```
- catch 메서드는 then 메서드와 마찬가지로 언제나 프로미스를 반환함

<br>

#### `Promise.prototype.finally`
- finally 메서드는 한 개의 콜백 함수를 인수로 전달 받음
- finally 메서드의 콜백 함수는 프로미스 성공 또는 실패와 상관없이 무조건 한 번 호출됨
- 프로미스의 상태와 상관없이 공통적으로 수행해야 할 처리 내용이 있을 때 유용
- finally 메서드도 then/catch 메서드와 마찬가지로 언제나 프로미스를 반환함 

  ```js
  new Promise(() => {})
    .finally(() => console.log('finally')) // finally
  ```

  #### (참고) `try...catch...finally` 문
  - try...catch...finally 문은 에러 처리를 구현하는 방법
  - 먼저 try 코드 블록이 실행됨
  - 이때 try 코드 블록에 포함된 문 중 에러가 발생하면 해당 에러는 catch 문의 err 변수에 전달되고 catch 코드 블록이 실행됨
  - finally 코드 블록은 에러 발생과 관계없이 반드시 한 번 실행됨
  - try...catch...finally 문으로 에러를 처리하면 프로그램이 강제 종료되지 않음

<br>


- 프로미스로 구현한 비동기 함수 get 을 사용해 후속처리를 해보면 아래와 같음
  ```js
    // GET 요청을 위한 비동기 함수
    const promiseGet = url => {
      return new Promise((resolve, reject) => {
        const xhr = new XMLHttpRequest();   
        xhr.open('GET', url);
        xhr.send();

        xhr.onload = () => {
          if (xhr.status === 200){
            // 성공하면 resolve 함수 호출
            resolve(JSON.parse(xhr.response));
          } else {
            // 에러 처리를 위해 reject 함수 호출
            reject(new Error(xhr.status));
          }
        };
      });
    };

    // promiseGet 함수는 프로미스를 반환
    promiseGet('https://jsonplaceholder.typicode.com/posts/1')
      .then(res => console.log(res))
      .catch(err => console.log(err))
      .finally(() => console.log('Bye'));
    ```

<br>

### 프로미스의 에러 처리
- 프로미스는 에러를 문제없이 처리할 수 있음
- 비동기 처리에서 발생한 에러는 then 메서드의 두 번째 콜백 함수로 처리할 수 있음
  ```js
  // 위 예제와 이어짐
  const wrongUrl = 'https://xxx.com/1';

  // 잘못된 URL이 지정되었기 때문에 에러 발생
  promiseGet(wrongUrl).then(
    res => console.log(res)
    err => console.error(err)
  ); // Error: 404
  ```
- 단, then 메서드의 두 번째 콜백 함수는 첫 번째 콜백 함수에서 발생한 에러를 캐치하지 못하고 코드가 복잡해져 가독성이 떨어짐

<br>


- 또한 프로미스 후속 처리 메서드 catch 로도 처리 가능
  ```js
  const wrongUrl = 'https://xxx.com/1';

  // 잘못된 URL이 지정되었기 때문에 에러 발생
  promiseGet(wrongURl)
    .then(res => console.log(res))
    .catch(undefined, err => console.log(err)); // Error: 404
  ```
- catch 메서드를 호출하면 내부적으로 then(undefined, onRejected)을 호출하므로 위 예제처럼 처리됨(굳이 적지 않아도 됨)
- catch 메서드를 모든 then 메서드를 호출한 이후에 호출하면 비동기 처리에서 발생한 에러 뿐만 아니라 then 메서드 내부에서 발생한 에러까지 모두 캐치가 가능

  ```js
  promiseGet('https://github.com/bboyooning');
    .then(res => console.xxx(res))
    .catch(err => console.log(err)); // TypeError: console.xxx is not a function
  ```

- 또한 가독성이 좋고 명확하기 때문에 catch 메서드에서 에러 처리를 하는 것이 좋음

<br>

### 프로미스 체이닝
- 프로미스는 then, catch, finally 후속 처리 메서드를 통해 콜백 헬을 해결함
  ```js
  const url = 'https://github.com/bboyooning';

  // id가 1인 post의 userId를 취득
  promiseGet(`${url}/posts/1`)
    // 취득한 post의 userId로 user 정보 취득
    .then(({ userId }) => promiseGet(`${url}/users/${userId}`))
    .then(userInfo => console.log(userInfo))
    .catch(err => console.err(err));
  ```
- then -> then -> catch 순으로 후속 처리 메서드를 호출
- then, catch, finally 후속 처리 메서드는 언제나 프로미스를 반환하므로 연속적으로 호출이 가능
- 이를 `프로미스 체이닝` 이라고 함
- 후속 처리 메서드의 콜백 함수는 프로미스의 비동기 처리 상태가 변경되면 선택적으로 호출됨
- 후속 처리 메서드의 콜백 함수는 다음과 같이 인수를 전달받으며 호출됨
- 프로미스는 프로미스 체이닝을 통해 비동기 처리 결과를 전달받아 후속 처리를 하므로 콜백 헬이 발생하지 않음
- 다만 프로미스도 콜백 패턴을 사용하므로 콜백 함수를 사용하지 않는 것은 아님

<br>

- 콜백 패턴은 가독성이 좋지 않음
- 이는 `ES8` 에서 도입된 `async/await` 을 통해 해결이 가능
- async/await 를 사용하면 프로미스의 후속 처리 메서드 없이 마치 동기 처리처럼 프로미스가 처리 결과를 반환하도록 구현 가능
  ```js
  const url = 'https://github.com/bboyooning';

  (async () => {
    // id가 1인 post의 userId를 취득
    const { userId } = await promiseGet(`${url}/posts/1`);
    // 취득한 post의 userId로 user 정보 취득
    const userInfo = await promiseGet(`${url}/users/${userId}`);

    console.log(userInfo);
  })();
  ```
  <br>

### 프로미스의 정적 메서드
- 프로미스는 주로 생성자 함수로 사용되지만 함수도 객체이므로 메서드를 가질 수 있음
- 프로미스는 5가지 정적 메서드를 제공함

#### `Promise.resolve / Promise.reject`
- Promise.resolve 와 Promise.reject 메서드는 이미 존재하는 값을 래핑하여 프로미스를 생성하기 위해 사용됨
  ```js
  const resolvedPromise = Promise.resolve([1,2,3]);
  // const resolvedPromise = new Promise(resolve => resolve([1,2,3]);
  resolvedPromise.then(console.log); // 1,2,3;

  const rejectedPromise = Promise.rejected(new Error('Error!'));
  // const rejectedPromise = new Promise((_, reject) => reject(new Error('Error!')));
  rejectedPromise.catch(console.log); // Error: Error!
  ```
#### `Promise.all`
- Promise.all 메서드는 여러 개의 비동기 처리를 모두 병렬 처리할 때 사용됨
  ```js
  const requestData1 = () => new Promise(resolve => setTimeout(() => resolve(1), 3000));
  const requestData2 = () => new Promise(resolve => setTimeout(() => resolve(2), 2000));
  const requestData3 = () => new Promise(resolve => setTimeout(() => resolve(3), 1000));

  // 세 개의 비동기 처리를 병렬로 처리
  Promise.all([requestData1(), requestData2(), requestData3()])
    .then(console.log) // 약 3초 소요 -> [ 1, 2, 3 ]
    .catch(console.error);
  ```
- Promise.all 메서드는 프로미스를 요소로 갖는 배열 등의 이터러블을 인수로 전달 받음
- 그리고 전달받은 모든 프로미스가 모두 fulfilled 상태가 되면 모든 처리 결과를 배열에 저장해 새로운 프로미스를 반환함
- 따라서 해당 메서드가 종료하는 데 걸리는 시간은 가장 늦게 fulfilled 상태가 되는 프로미스의 처리 시간보다 조금 더 김
- 이때 첫 번째 프로미스가 가장 나중에 fulfilled 상태가 되어도 Promise.all 메서드는 첫 번째 프로미스가 resolve 한 처리 결과부터 차례대로 배열에 저장해 그 배열을 resolve 하는 새로운 프로미스를 반환함
- 즉, 처리 순서가 보장됨
- 또한 Promise.all 메서드는 인수로 전달받은 배열의 프로미스가 하나라도 rejected 상태가 되면 나머지 프로미스가 fulfilled 상태가 되는 것을 기다리지 않고 즉시 종료함
  ```js
  Promise.all([
    new Promise(resolve => setTimeout(() => resolve(1), 3000));
    new Promise(resolve => setTimeout(() => resolve(2), 2000));
    new Promise(resolve => setTimeout(() => resolve(3), 1000));
  ])
  .then(console.log) // 3
  .catch(console.error)
  ```

#### `Promise.race`
- Promise.all 메서드와 동일하게 프로미스를 요소로 갖는 배열 등의 이터러블을 인수로 전달 받음
- 하지만 모든 프로미스가 fulfilled 상태가 되는 것을 기다리지 않고, 가장 먼저 fulfilled 상태가 된 프로미스 처리 결과를 resolve 하는 새로운 프로미스를 반환
  ```js
  Promise.race([
    new Promise(resolve => setTimeout(() => reject(new Error('Error 1')), 3000)),
    new Promise(resolve => setTimeout(() => reject(new Error('Error 2')), 2000)),
    new Promise(resolve => setTimeout(() => reject(new Error('Error 3')), 1000)),
  ])
    .then(console.log) // 3
    .catch(console.error);
  ```
- 또한 전달된 프로미스가 하나라도 rejected 상태가 되면 에러를 reject하는 새로운 프로미스를 즉시 반환
  ```js
  Promise.race([
    new Promise((_, reject) => setTimeout(() => reject(new Error('Error 1')), 3000)),
    new Promise((_, reject) => setTimeout(() => reject(new Error('Error 2')), 2000)),
    new Promise((_, reject) => setTimeout(() => reject(new Error('Error 3')), 1000)),
  ])
  .then(console.log)
  .catch(console.error); // Error: Error 3
  ```

#### `Promise.allSettled`
- Promise.allSettled 메서드는 프로미스를 요소로 갖는 배열 등의 이터러블을 인수로 전달 받음
- 전달받은 프로미스가 모두 settled 상태(비동기 처리가 수행된 상태, fulfilled 또는 rejected)가 되면 처리 결과를 배열로 반환함
- 이때 반환한 배열에는 fulfilled 또는 rejected 상태와는 상관없이 메서드가 인수로 전달받은 모든 프로미스들의 처리 결과가 담겨 있음

<br>

### 마이크로태스크 큐
- 어떤 순서로 로그가 출력될까?

  ```js
  setTimeout(() => console.log(1), 0);

  Promise.resolve()
    .then(() => console.log(2))
    .then(() => console.log(3));
  ```
- 프로미스의 후속 처리 메서드도 비동기로 동작하므로 1 -> 2 -> 3 순으로 출력할 것 같지만, 
- `2 -> 3 -> 1` 로 출력됨
- 그 이유는 프로미스의 후속 처리 메서드의 콜백 함수는 태스크 큐가 아니라 `마이크로태스크 큐` 에 저장되기 때문
- 마이크로태스크 큐는 태스크 큐와는 별도의 큐 임
- 마이크로태스크 큐에는 프로미스의 후속 처리 메서드의 콜백 함수가 일시 저장됨
- 그 외의 비동기 함수의 콜백 함수나 이벤트 핸들러는 태스크 큐에 일시 저장됨
- 콜백 함수나 이벤트 핸들러를 일시 저장한다는 점에서 태스크 큐와 동일하지만, 마이크로태스크 큐는 태스크 큐보다 우선순위가 높음
- 즉, 이벤트 루프는 콜 스택이 비면 먼저 마이크로태스크 큐에서 대기하고 있는 함수를 가져와 실행함
  <img src="https://uploads.disquscdn.com/images/9466d8aa53fc5b3e63a92858a94bb429df02bbd20012b738f0461343beaa6f90.gif?w=600&h=272">

- 이후 마이크로태스크 큐가 비면 태스크 큐에서 대기하고 있는 함수를 가져와 실행함

<br>

### fetch
- fetch 함수는 XMLHttpRequest 객체와 마찬가지로 HTTP 요청 전송 기능을 제공하는 클라이언트 사이드 Web API
- 사용법이 간단하고 프로미스를 지원하기 때문에 비동기 처리를 위한 콜백 패턴의 단점에서 자유로움
- fetch 함수에는 HTTP 요청을 전송할 URL과 HTTP 요청 메서드, HTTP 요청 헤더, 페이로드 등을 설정한 객체를 전달함
  ```js
  const promise = fetch(url, [, options])
  ```
- fetch 함수는 HTTP 응답을 나타내는 Response 객체를 래핑한 Promise 객체를 반환하므로 then 을 통해 프로미스가 resolve 한 Response 객체를 전달받을 수 있음
- Response 객체는 HTTP 응답을 나타내는 다양한 프로퍼티를 제공함
  ```js
  fetch('https://jsonplaceholder.typicode.com/todos/1')
  // response 는 HTTP 응답을 나타내는 Response 객체
  // json 메서드를 사용하여 Response 객체에서 HTTP 응답 몸체를 취득하여 역직렬화 함
    .then(response => response.json())
    // json은 역직렬화된 HTTP 응답 몸체
    .then(json => console.log(json));
  ```

- fetch 함수를 사용할 때는 에러 처리에 주의해야 함
  ```js
  const wrongUrl = 'https://jsonplaceholder.typicode.com/xxx/1';

  fetch(wrongUrl)
    .then(() => console.log('ok'))
    .catch(() => console.log('error'));
  ```
- 부적절한 URL 지정으로 에러가 발생하고, catch 메서드에 의해 'error' 가 출력될 것 같지만 'ok' 가 출력됨
- fetch 함수가 반환하는 프로미스는 기본적으로 404 나 500 과 같은 HTTP 에러가 발생해도 에러를 reject 하지 않고, 
- 불리언 타입의 ok 상태를 false로 설정한 Response 객체를 resolve 함
- 오프라인 등 네트워크 장애나 CORS 에러에 의해 요청이 완료되지 못한 경우에만 프로미스를 reject 함
- 따라서 fetch 함수를 사용할 때는 아래와 같이 fetxh 함수가 반환한 프로미스가 resolve한 불리언 타입의 ok 상태를 확인해 명시적으로 에러 처리를 해야 함
  ```js
  const wrongUrl = 'https://jsonplaceholder.typicode.com/xxx/1';

  fetch(wrongUrl)
    // response 는 HTTP 응답을 나타내는 Response 객체
    .then(response => {
      if(!response.ok) throw new Error(response.statusText);
      return response.json();
    })
    .then(todo => console.log(todo))
    .catch(err => console.error(err));
  ```

- 참고로 `axios` 는 모든 HTTP 에러를 reject 하는 프로미스를 반환함
- 따라서 모든 에러를 catch 에서 처리할 수 있어 편리함
- 또한 axios는 인터셉터, 요청 설정 등 fetch 보다 다양한 기능을 지원함

- fetch 함수를 통해 HTTP 요청을 전송할 때, 함수에 첫 번째 인수로 HTTP 요청을 전송할 URL 과 두번째 인수로 HTTP 요청 메서드, HTTP 요청 헤더, 페이로드 등을 설정한 객체를 전달함

  ```js
  const request = {
    get(url){
      return fetch(url);
    },
    post(url, payload){
      return fetch(url, {
        method: 'POST',
        headers: { 'content-Type': 'application/json' },
        body: JSON.stringify(payload)
      });
    },
    patch(url, payload){
      return fetch(url, {
        method: 'PATCH',
        headers: { 'content-Type': 'application/json' },
        body: JSON.stringify(payload)
      });
    },
    delete(url){
      return fetch(url, { method: 'DELETE' });
    }
  };
  ```