---
layout: post
title: Typescript - primitive type이 아닌 기본 타입
date: 2022-09-13 21:07:41 +0900
category: TypeScript
---

### <span style="color:#febc68;font-weight:bold">object</span>
javascript에서 object는 직접적인 값을 가지고 있지 않고, 값을 가지고 있는 곳을 가리키는

typescript에서의 object는 Primitive type이 아닌 것을 나타내고 싶을 때 사용한다.

```javascript
    // a는 "{name:'joj', age: 30}" type이다. =  object 리터럴 타입
    const a = {name:'joj', age: 30}

    // b는 Object type이다.
    const B = Object.create({name:'joj', age: 30})

```
### <span style="color:#febc68;font-weight:bold">Array</span>
같은 타입의 요소을 모아놓은 자료형
!! 배열 안에 있는 요소들은 모두 같은 타입이라는 것을 주의해야한다!!  
!! 배안 안 요소가 다른 타입일 때 유니온을 사용해야 한다!!

```javascript
    // 공통요소[] or Array<공통요소>로 표현한다.
    let list:number[] = [1,2,3]
    let list:Array<number> = [1,2,3]
```
