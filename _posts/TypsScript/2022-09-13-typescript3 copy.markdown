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

### <span style="color:#febc68;font-weight:bold">Tuple</span>
다른 타입의 요소를 모아놓은 자료형
!! 배열 안에 있는 요소가 다른 타입일 수 있으나, 각 인덱스 타입도 불변이기에 값을 할당할 때 인덱스 타입과 같은 타입의 값을 입력해야한다.
```javascript
    let x:[string, number];
```

### <span style="color:#febc68;font-weight:bold">any</span>
의미 그대로 어떤 타입이든 가능한 타입으로
활용성,융통성이 좋아 편리하지만,
너무 남발하게 되면 타입의 안전성을 잃게 되고   
컴파일 타임에서 타입체크가 정상적으로 이워지지 않기 떄문에  
최대한 쓰지 않는 게 좋다.  

```javascript
    function returnAny(msg):any {
        console.log(msg)
    }

    const any1 = returnAny('아무거나 리턴');
```

### <span style="color:#febc68;font-weight:bold">unknown</span>
any로 인해 생길 수 있는 타입의 불안전성을 보완하기 위한 타입이다.
동적 콘텐츠(예를 들어 API)와 같이 타입을 아직 알 수 없는 변수를 작성해야할 때  
any를 사용할 수도 있지만, unknown 타입을 작성하여 변수의 타입이 무엇이든 될 수 있음을 알려줄 수 있다.
```javascript
    declare const maybe : unknown;
    
    const aNumber: number = maybe

    if(maybe === true){
        // error X
        const aBoolean: boolean = maybe;
        // error O
        const aString: string = maybe;
    }
    if(typeof maybe === "string"){
        // error X
        const aString: string = maybe;
        // error O
        const aBoolean: boolean = maybe;
    }
```
즉, any와 달리 unknown은 타입을 확정지어준 후에 사용할 수 있고,   
확정지은 타입과 다른 타입을 할당하면 에러가 나기 때문에 보다 안전하게 사용할 수 있다!

### <span style="color:#febc68;font-weight:bold">never</span>
never 타입은 값의 공집합이기 때문에 any타입의 값을 포함해 어떤 값도 가질 수 없다.  

그렇다면 never 타입은 왜 필요할까?!  
숫자 중 0처럼 아무것도 없음을 나타낼수 있는 타입이 필요했기 때문이다.  

never 타입을 많이 사용하지는 않지만, 적절하게 사용될 때가 있다.
대표적으로는 허용할 수 없는 함수 매개변수에 제한을 가하는 경우  
혹은 switch, if-else문의 상황을 보장하는 용도로 사용된다.
```javascript
    function error(msg:string):never{
        throw new Error(msg)
    }

    function fail(){
        return error("failed")
    }

    function infiniteLoop():never {
        while (true) {
            
        }
    }
```

### <span style="color:#febc68;font-weight:bold">void</span>
void는 결과 값을 반환하지 않는 함수에 설정한다.

![typescript type](../../../../public/img/typescript.png)