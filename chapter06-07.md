# 06장 ~ 07장 정리

## 데이터 타입
- 데이터 타입이란 값의 종류를 의미한다.
- 데이터 타입은 원시 타입과 객체 타입(참조타입)으로 분류한다.
  - 원시 타입
    - 숫자 타입
    - 문자열 타입
    - 불리언 타입
    - undefined 타입 (선언된 변수에 암묵적으로 할당되는 값 - 컴퓨터가 넣는 값)
    - 심벌 타입
  - 객체 타입 = 참조타입 (객체, 함수, 배열 등이 있으며 주소 값을 갖는다)
  ``` javascript
    // 객체
    const user = {
        name: 'cmhui',
        age: 9,
        key: value, // property
        hello: function() {
            console.log('hello world');
        } // property 에 function 이 들어가면 '메소드'
    }

    // 객체의 프로퍼티 접근법 
    // dot notation
    let userName = user.name;
    console.log(userName);

    // bracket notaion
    let userAge = user['age'];
    console.log(userAge);
  ```

- 자바스크립트 변수는 할당에 의해 타입이 결정되고 재 할당에 의해 타입은 언제든지 변할 수 있다. 이런 특징을 **동적타이핑** 이라 한다.
- 동적 타이핑과 반다되는 **정적타입 언어는** 데이터 타입을 사전에 선언해야 하는 C, Java.. 등이 있다.

## 연산자 
- 연산자 종류
    ``` javascript
    5 + 4 = 9 // = 9 산술 연산자
    'My name is ' + 'hui' // = 'My name is hui' 문자열 연결 연산자
    age = 18 // = 18 할당 연산자
    4 > 5 // = false 비교 연산자
    true && false // = false 논리 연산자
    typeof 'Hello' // = string 타입 연산자
    ```
- **이항 산술 연산자** : 덧셈, 뺄셈, 곱셈, 나눗셈, 나머지 (+, -, \*, /, %)
    > 증가/감소 연산자는 피연산자의 값을 변경하는 효과가 있다.  
    > 또한, 연산자의 위치에 따라 의미가 달라진다.
    ``` javascript
    // 증가, 감소 (++, --)
    var x = 5, result;

    result = x++; //선할당 후증가
    result = ++x; //선증가 후할당
    result = x--; //선할당 후감소
    result = --x; //선감소 후할당

    // + 단항 연산자 (데이터타입을 숫자로 변환해줌. 단, 아무런 부수 효과 없음)
    +10; // 10
    +(-10) // 10

    var x = '1';
    console.log(+x); // 1

    x = true;
    console.log(+x); // 1 (암묵적 타입변환 / 1은 truthy한 값)

    x = false;
    console.log(+x); // 0 (암묵적 타입변환 / 0은 falsy한 값)

    x = 'Hello';
    console.log(+x); // NaN (문자열을 숫자로 타입변환할 수 없다)

    // - 단항 연산자 (부호를 반전)
    -(-10); // 10
    ```

- **할당 연산자**는 좌항의 변수에 값을 할당하므로 변수 값이 변하는 부수효과가 있다
``` javasciprt
// 할당 연산자
x += 9 // 동일표현 -> x = x + 9
```
- **비교 연산자**  
  - **동등 비교 연산자(==, !=)** 는 타입이 달라도 암묵적 타입 변환을 통해 타입을 일치시키며 동등하게 해석한다.
  - 이처럼 동등 비교 연산자는 예측하기 어려운 결과를 만들어내므로 사용하지 않는 것이 좋고 대신 **일치비교(===, !==)**를 사용한다.
  - 일치 비교 연산자는 값과 타입이 모두 같을 경우에 true를 반환한다.
  - **특이점**
    - NaN은 자신과 일치하지 않는 유일한 값으로 false를 반환한다.
    - 양과 음의 '0'을 비교하면 결과는 모두 true다.
- **삼항 조건 연산자**
  > 조건식 ? 조건식이 true일 때 반환할 값 : 조건식이 false일 때 반환할 값
    ``` javascript
    var result = score >= 90 ? 'pass' : 'fail';
    ```
- 삼항 조건 연산자는 if...else문과 유사하게 처리할 수 있다. 차이점은, 삼항 조건 연산자 표현식은 값처럼 사용할 수 있지만 if...else문은 값처럼 사용할 수 없다 (if...else문은 표현식이 아닌 문이기 때문)
- 조건에 따라 **어떤 값을 결정** 해야 한다면 if...else문보다 **삼항 조건 연산자** 를 사용하는 편이 유리하고 **수행해야할 문이 하나가 아니라 여러개** 일 경우 **if...else문**의 가독성이 더 좋다
- **논리 연산자** (|| : or, && : and, ! : not)
- **typeof 연산자** 는 피연산자의 데이터 타입을 문자열로 반환한다
``` javascript
    typeof '' // string
    typeof 1 // number
    typeof true // boolean
    typeof undefined // undefined
    typeof function (){} // function

    // 유의
    typeof NaN // number  
    typeof null // object  
    // null값을 typeof로 연산하면 object를 반환하므로, null 타입인지를 확인할 때에는 typeof 대신 일치 연산자(===)를 사용하자

    typeof [] // object   
    typeof {} // object    
    typeof new Date() // object  
    typeof /test/gi // object 추후 학습  
    typeof Symbol() // symbol 추후 학습  
    typeof undeclared; // undefined  
    // 선언하지 않은 식별자를 typeof로 연산하면 ReferenceError가 발생하지 않고 undefined를 반환한다
```
# 06장 ~ 07장 정리

## 데이터 타입
- 데이터 타입이란 값의 종류를 의미한다.
- 데이터 타입은 원시 타입과 객체 타입(참조타입)으로 분류한다.
  - 원시 타입
    - 숫자 타입
    - 문자열 타입
    - 불리언 타입
    - undefined 타입 (선언된 변수에 암묵적으로 할당되는 값 - 컴퓨터가 넣는 값)
    - 심벌 타입
  - 객체 타입 = 참조타입 (객체, 함수, 배열 등이 있으며 주소 값을 갖는다)
  ``` javascript
    // 객체
    const user = {
        name: 'cmhui',
        age: 32
        key: value, // propertie
        hello: function() {
            console.log('hello world');
        } // propertie 에 function 이 들어가면 '메소드' 지랄하고있네
    }

    // 객체의 프로퍼티 접근법 
    // dot notation
    let userName = user.name;
    console.log(userName);

    // bracket notaion
    let userAge = user['age'];
    console.log(userAge);
  ```

- 자바스크립트 변수는 할당에 의해 타입이 결정되고 재 할당에 의해 타입은 언제든지 변할 수 있다. 이런 특징을 **동적타이핑** 이라 한다.
- 동적 타이핑과 반다되는 **정적타입 언어는** 데이터 타입을 사전에 선언해야 하는 C, Java.. 등이 있다.

## 연산자 
- 연산자 종류
    ``` javascript
    5 + 4 = 9 // = 9 산술 연산자
    'My name is ' + 'hui' // = 'My name is hui' 문자열 연결 연산자
    age = 18 // = 18 할당 연산자
    4 > 5 // = false 비교 연산자
    true && false // = false 논리 연산자
    typeof 'Hello' // = string 타입 연산자
    ```
- **이항 산술 연산자** : 덧셈, 뺄셈, 곱셈, 나눗셈, 나머지 (+, -, \*, /, %)
    > 증가/감소 연산자는 피연산자의 값을 변경하는 효과가 있다.  
    > 또한, 연산자의 위치에 따라 의미가 달라진다.
    ``` javascript
    // 증가, 감소 (++, --)
    var x = 5, result;

    result = x++; //선할당 후증가
    result = ++x; //선증가 후할당
    result = x--; //선할당 후감소
    result = --x; //선감소 후할당

    // + 단항 연산자 (데이터타입을 숫자로 변환해줌. 단, 아무런 부수 효과 없음)
    +10; // 10
    +(-10) // 10

    var x = '1';
    console.log(+x); // 1

    x = true;
    console.log(+x); // 1 (암묵적 타입변환 / 1은 truthy한 값)

    x = false;
    console.log(+x); // 0 (암묵적 타입변환 / 0은 falsy한 값)

    x = 'Hello';
    console.log(+x); // NaN (문자열을 숫자로 타입변환할 수 없다)

    // - 단항 연산자 (부호를 반전)
    -(-10); // 10
    ```

- **할당 연산자**는 좌항의 변수에 값을 할당하므로 변수 값이 변하는 부수효과가 있다
``` javasciprt
// 할당 연산자
x += 9 // 동일표현 -> x = x + 9
```
- **비교 연산자**  
  - **동등 비교 연산자(==, !=)** 는 타입이 달라도 암묵적 타입 변환을 통해 타입을 일치시키며 동등하게 해석한다.
  - 이처럼 동등 비교 연산자는 예측하기 어려운 결과를 만들어내므로 사용하지 않는 것이 좋고 대신 **일치비교(===, !==)**를 사용한다.
  - 일치 비교 연산자는 값과 타입이 모두 같을 경우에 true를 반환한다.
  - **특이점**
    - NaN은 자신과 일치하지 않는 유일한 값으로 false를 반환한다.
    - 양과 음의 '0'을 비교하면 결과는 모두 true다.
- **삼항 조건 연산자**
  > 조건식 ? 조건식이 true일 때 반환할 값 : 조건식이 false일 때 반환할 값
    ``` javascript
    var result = score >= 90 ? 'pass' : 'fail';
    ```
- 삼항 조건 연산자는 if...else문과 유사하게 처리할 수 있다. 차이점은, 삼항 조건 연산자 표현식은 값처럼 사용할 수 있지만 if...else문은 값처럼 사용할 수 없다 (if...else문은 표현식이 아닌 문이기 때문)
- 조건에 따라 **어떤 값을 결정** 해야 한다면 if...else문보다 **삼항 조건 연산자** 를 사용하는 편이 유리하고 **수행해야할 문이 하나가 아니라 여러개** 일 경우 **if...else문**의 가독성이 더 좋다
- **논리 연산자** (|| : or, && : and, ! : not)
- **typeof 연산자** 는 피연산자의 데이터 타입을 문자열로 반환한다
``` javascript
    typeof '' // string
    typeof 1 // number
    typeof true // boolean
    typeof undefined // undefined
    typeof function (){} // function

    // 유의
    typeof NaN // number  
    typeof null // object  
    // null값을 typeof로 연산하면 object를 반환하므로, null 타입인지를 확인할 때에는 typeof 대신 일치 연산자(===)를 사용하자

    typeof [] // object   
    typeof {} // object    
    typeof new Date() // object  
    typeof /test/gi // object 추후 학습  
    typeof Symbol() // symbol 추후 학습  
    typeof undeclared; // undefined  
    // 선언하지 않은 식별자를 typeof로 연산하면 ReferenceError가 발생하지 않고 undefined를 반환한다
```
