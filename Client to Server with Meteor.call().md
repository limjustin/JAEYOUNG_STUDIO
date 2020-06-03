## Client to Server with Meteor.call()

#### Meteor Developers

![image-20200603000351198](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20200603000351198.png)

Before you read,

- stub (methods)

  - https://stackoverflow.com/questions/17510707/what-is-a-stub-method-in-meteorjs

  - the ones defined via `Meteor.methods`

  - In Meteor, these stubs allow you to have **latency compensation**. This means that when you call one of these stubs with `Meteor.call` it might **take some time** for the **server** to **reply with the return value** of the stub.



Meteor.call()

- https://docs.meteor.com/api/methods.html#Meteor-apply

- Arguments
  - name, args, **asyncCallback**
- Definition
  - It will run the method on the server.
  - When the method is complete, the callback will be called with two arguments: `error` and `result`.
  - If an error was thrown, the `error` will be the exception object. Otherwise, `error` will be `undefined` and the return value(possibly `undefined`) will be in `result`.



#### stackoverflow

##### Meteor.methods returns undefined

- https://stackoverflow.com/questions/17460123/meteor-methods-returns-undefined

- Server methods calls in Meteor are documented to be asynchronous.
- On the client, if you do not pass a callback and you are not inside a stub, call will return `undefined`, and you will have no way to get the return value of the method.



#### Meteor Forums

- https://forums.meteor.com/t/meteor-method-call-comes-back-as-undefined/14091/9

- `Meteor.call()` sends a message to the server, and **server returns immediately**. It does **not wait for the response**. So the **return value** of `Meteor.call()` is `undefined`.



## What is Asynchronous Call?

#### 자바스크립트 비동기 처리와 콜백 함수

- https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/

- 비동기 처리란?

  - 특정 코드의 연산이 끝날 때까지 코드의 실행을  멈추지 않고 다음 코드를 먼저 실행하는 것

- 비동기 처리가 필요한 이유

  - 화면에서 서버로 데이터를 요청하였을 때, 서버가 언제 그 요청에 대한 응답을 줄지 모르는데 마냥 다른 코드를 실행 안하고 응답만 계속 기다릴 순 없기 때문.
  - 비동기 처리가 아니고 동기 처리라면 코드를 실행하고 기다리고, 실행하고 기다리고가 계속 반복될 것이며, 실행하는데 엄청난 시간이 걸릴 것임.

- `setTimeout()`과 관련된 비동기 처리 사례

  ```javascript
  // #1
  console.log('Hello');
  // #2
  setTimeout(function() {
      console.log('Bye');
  }, 3000);
  // #3
  console.log('Hello Again');
  ```

  - 예상 결과 : 

  ​		Hello

  ​		Bye (3초 있다가)

  ​		Hello Again

  - 실제 결과 :

    Hello

    Hello Again

    Bye (3초 있다가)
  
- 실생활 예제

  - 콜백 함수의 동작 방식은 식당 자리 예약과 비슷함.
  - 어느 음식점을 방문하였을 때, 사람이 많으면 대기자 명단에 이름을 쓴 다음에 자리가 날 때까지 주변 식당을 돌아다니거나 쇼핑을 할 수 있음. (비동기 방식 처리)
  - 만약 식당에서 자리가 생기게 되면, 전화로 자리가 났다고 연락이 옴. (콜백 함수가 호출되는 시점)
  - 즉, **데이터가 준비된 시점**에서만 우리가 원하는 동작을 수행할 수 있게 하는 것임.