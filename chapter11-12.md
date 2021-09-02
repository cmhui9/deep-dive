# 11장 - 12장 정리

## 원시값
* 원시값(원시 타입의 값)의 값은 변경 불가능한 값
* 원시값을 자체를 변경하는 것은 불가능하지만, 변수에 새로운 값을 재할당하는 것은 가능하다.
  ```javascript
  var score = 100;

  // copy 변수에는 score 변수의 값 '100'이 복사되어 할당된다
  var copy = score;

  console.log(score, copy); // 100 100
  console.log(score === copy); // true
  ```
* score와 copy 변수는 숫자 값 100을 갖는다는 점에서 동일하다. 하지만 **두 변수의 값은 다른 메모리 공간에 저장된 별개의 값이다.**
* 그러므로 어느 한쪽에서 재할당을 통해 값을 변경하더라도 서로 간섭할 수 없다.
<br>
<br>

## 객체
* 객체(객체 타입의 값)는 변경 가능한 값
* 객체는 재할당 없이 프로퍼티를 동적으로 추가할 수도 있고 프로퍼티 값을 갱신할 수도 있으며, 프로퍼티 자체를 삭제할 수도 있다.
* 여러 개의 식별자(변수명)가 하나의 객체를 공유할 수 있다. (이러한 특성에 따른 부작용이 발생한다.)
  ```javascript
  var person = {
      name: 'Choi'
  };

  var copy = person;
  ```
  * 원본 person과 사본 copy는 저장된 메모리 주소(주소값)는 다르지만 동일한 참조 값을 갖는다. 
  __(두 가지 모두 동일한 객체를 가리킨다.)__
  * 이것은 __두 개의 식별자가 하나의 객체를 공유__ 한다는 것을 의미한다.
  * 원본 또는 사본 중 어느 한쪽에서 객체를 변경 (변수에 새로운 객체를 재할당하는 것이 아니라 객체의 프로퍼티 값을 변경하거나 프로퍼티를 추가/삭제) 하면 서로 영향을 주고받는다.
  ```javascript
  var person = {
      name: 'Choi'
  };

  var copy = person; // 참조 값 복사
  
  console.log(copy === person); // true

  copy.name = 'hui'; // copy를 통해 객체를 변경한다.
  person.nation = 'Korea'; // person을 통해 객체를 변경한다.

  console.log(person); // {name: 'hui', nation: 'Korea'}
  console.log(copy); // {name: 'hui', nation: 'Korea'}
  // copy와 person은 동일한 객체를 가리킨다.
  // 따라서 어느 한쪽에서 객체를 변경하면 서로 영향을 주고 받는다.
  ```
<br>
<br>

## 함수
...
  