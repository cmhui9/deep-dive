# 01장 - 05장 정리

### 자바스크립트

-   자바스크립트 ECMA 스크립트는 해마다 버전업 되고있다
-   V8 자바스크립트 엔진은 구글 크롬에서 사용하는 엔진이다
-   Node.js 는 서버사이드 애플리케이션 개발에 주로 사용된다
-   SPA 프레임워크란 페이지 이동 없이 특정영역만 새로 모듈을 호출하여 데이터를 바인딩하는 것으로 React, Vue, Angular, Svelte 등이 있다
-   자바스크립트는 인터프리터 언어로서 런타임에서 문 단위로 한 줄씩 실행한다
-   컴파일러 언어는 코드 실행 전 컴파일 단계에서 소스코드 전체를 한번에 머신 코드로 한번에 변환 후 실행한다 (java, c 등)
-   크롬 개발자도구에서 source 패널은 로딩된 웹페이지의 자바스크립트 코드를 디버깅할 수 있다
-   디버깅이란, 코드 라인에 브레이크포인트를 걸고 에러가 발생한 지점을 확인하는 방법이다

### 변수

-   변수는 값저장을 하는 것 이며, 재사용 할 수 있는 특징이 있다
-   식별자는 변수명을 뜻한다
-   변수를 사용하려면 반드시 선언이 필요한고 선언할 때는 var, let, cont 키워드를 사용한다
-   변수 선언과 값의 할당을 하나의 문으로 단축 표현해도 2개의 문으로 각각 실행한다
-   주의할 점은 실행시점이 다른 것인데 1️⃣'변수 선언'은 소스코드가 순차적으로 실행되는 시점인 런타임 이전에 먼저 실행되지만 2️⃣'값의 할당'은 소스코드가 순차적으로 실행되는 시점인 런타임에 실행된다

    ```
    	console.log(foo); // undefined 
    	var foo; // 1️⃣변수 선언 
    	foo = 100; // 2️⃣값의 할당 
    	// var foo = 100; 과 동일 
    	console.log(foo); // 100​
    ```

      
-   변수에 저장된 값을 변경할 수 없으면 **상수** 라고 한다
-   const 키워드를 사용해 선언한 변수는 재할당이 금지되므로 상수로 표현할 수 있다 (하지만 반드시 상수만을 위해 사용하지는 않는다)
-   변수/함수에는 카멜케이스 사용, 생성자 함수/클래스이름에는 파스칼케이스 사용

    ```
    	var firstName; // 카멜케이스
    	var FirstName; // 파스칼케이스
    ```


### 표현식과 문

-   '값'이란 표현식이 평가되어 생성된 결과를 말한다
-   '리터럴'이란 사람이 이해할 수 있는 문자 또는 약속된 기호를 사용해 값을 생성하는 표기법  
    ex) 'Hello' 문자열 리터럴, true/false 불리언 리터럴, { name: 'Choi', address: 'Bucheon' } 객체 리터럴 등
-   '표현식'이란 값으로 평가될 수 있는 문이다 (위 리터럴은 값으로 평가되므로 표현식에 속한다)
-   '문'이란 프로그램을 구성하는 기본 단위이자 최소 실행 단위이며 명령문이라고도 부른다
-   문은 선언문, 할당문, 조건문, 반복문 등으로 구분할 수 있다
-   표현식은 문의 일부일 수도 있고 그 자체로 문이 될 수 있다

```
	var a; // 변수 선언문은 값이 아니므로 표현식이 아니고 문이된다
	a = 1 + 2; // 이 코드 라인은 표현식이면서 완전한 문이기도 하다
```