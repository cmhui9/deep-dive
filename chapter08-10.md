# 08장 - 10장 정리

## 제어문
```javascript
// 블록문
{
    var foo = 10;
}

// 제어문
var x = 1;
if (x < 10) {
    x++;
}

// 함수 선언문
function sum(a, b) {
    return a + b;
}
```

- **조건문**은 주어진 조건식의 평가 결과에 따라 코드 블록(블록문)의 실행을 결정한다.
- 조건식은 불리언 값으로 평가될 수 있는 표현식이다.
- 자바스크립트는 **if...else** 문과 **switch** 문으로 두 가지 조건문을 재공한다.
```javascript
// if...else 문
if (조건식) {
    // 조건식이 true면 이 코드 블록이 실행된다
} else {
    // 조건식이 false면 이 코드 블록이 실행된다
}

// switch 문
switch (표현식) {
    case 표현식1:
        switch 문의 표현식과 표현식1이 일치하면 실행될 문;
        break;
    case 표현식2:
        switch 문의 표현식과 표현식2가 일치하면 실행될 문;
        break;
    default:
        switch 문의 표현식과 일치하는 case 문이 없을때 실행될 문;
}
```

- **반복문**은 조건식의 평가 결과가 true일 경우 코드 블록을 실행하고 그 후 조건식을 재평가 하여 여전히 참인 경우 코드 블록을 다시 실행한다. 이는 조건식이 false일 때까지 반복된다.
- 자바스크립트는 세 가지 반복문인 **for** 문, **while** 문, **do...while** 문을 제공한다.

```javascript
// for문
for (var i = 0; i < 2; i++) {
    console.log(i); // 0 1
}


// 중첩 for문
// 두 개의 주사위를 던져 두 눈의 합이 6이 되는 모든 경우의 수 출력
for (var i = 1; i <= 6; i++) {
    for (var j = 1; j <= 6; j++) {
        if (i + j === 6) console.log(`[${i}, ${j}]`);
    }
}
// 결과
[1, 5]
[2, 4]
[3, 3]
[4, 2]
[5, 1]


// while문
var count = 0;

while (count < 3){
    console.log(count); // 0 1 2
    count++;
}


// do while문
// do while문은 코드 블록을 먼저 실행하고 조건식을 평가한다.
var count = 0;

do {
    console.log(count); // 0 1 2
    count++;
} while (count < 3);
```

- **break**문은 레이블문, 반복문, switch문의 코드 블록을 탈출할때 사용한다.
- **continue**문은 반복문의 코드 블록 실행을 현 지점에서 중단하고 반복문의 증감식으로 실행 흐름을 이동 시킨다. break문처럼 반복문을 탈출하지는 않는다.

<br>
<br>

## 타입 변환과 단축 평가
- 개발자가 의도적으로 값의 타입을 변환하는 것을 **명시적 타입 변환** 또는 **타입 캐스팅**이라 한다.
- 자바스크립트 엔진에 의해 타입이 자동 변환되기도 하는데 이를 **암묵적 타입 변환** 또는 **타입 강제 변환**이라 한다.
- 자바스크립트 엔진은 불리언 타입이 아닌 값을 Truthy / Falsy 값으로 구분한다.
- **Falsy** 값
  - false
  - undefined
  - null
  - 0, -0
  - NaN
  - ''(빈 문자열)

- **Truthy** 값
  - falsy값 외의 모든 값은 모두 truthy값이다.

- **옵셔널 체이닝 연산자**
  - ES11에서 도입된 '?.' 연산자이다.
  - 좌항의 피연산자가 undefined 또는 null인 경우 undefined를 반환하고 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.
  - 논리 연산자 '&&'와 유사
```javascript
var elem = null;

var value = elem?.value;
console.log(value); // undefined
```

- **null 병합 연산자**
  - ES11에서 도입된 '??' 연산자이다.
  - 좌항의 피연산자가 undefined 또는 null인 경우 우항의 피연산자를 반환하고 그렇지 않으면 좌항의 피연산자를 반환한다.
  - 변수에 기본값을 설정할 때 유용하다.
  - 논리 연산자 '||'와 유사
```javascript
var foo = null ?? 'default string';
console.log(foo); // "default string"
```

<br>
<br>

## 객체 리터럴
- ES6에서 추가된 객체 리터럴의 확장 기능
- 프로퍼티 축약 표현
```javascript
// ES5
var x = 1, y = 2;

var obj = {
    x: x,
    y: y
};

console.log(obj); // {x: 1, y: 2}

// ES6
let x = 1, y = 2;

const obj = {x, y};

console.log(obj); // {x: 1, y: 2}
```

- 메서드 축약 표현
```javascript
// ES5
var obj = {
    name: 'Choi',
    sayHi: function(){
        console.log('Hi! ' + this.name);
    }
};

obj.sayHi(); // Hi! Choi


// ES6
const obj = {
    name: 'Choi',
    sayHi() {
        console.log('Hi! ' + this.name);
    }
};

obj.sayHi(); // Hi! Choi
```
