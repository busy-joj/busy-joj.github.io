---
layout: post
title: Typescript - type system
date: 2022-09-23 23:14:50 +0900
category: TypeScript
---
## <span style="color:#97cab3;font-weight:bold">type system</span>  
typescript에는 두가지 시스템이 있다. 
1. 컴파일러에게 사용하는 타입을 명시적으로 지정하는 시스템  
2. 타입을 명시적으로 지정하지 않는다면, 컴파일러가 자동으로 타입을 추론하는 시스템 

*타입을 추론하는 시스템에 필요한 옵션*
- nolmplicitAny : 추론 중 'any'라고 판단하게 되면, 컴파일러 에러를 발생시켜 명시적으로 지정하도록 유도한다.  
- strickNullChecks : 모든 타엡에 자동으로 포함되어 있는 'null'과 'undefined'를 제거해 에러를 줄인다.
- nolmplicitReturns : 함수 내에서 모든 코드가 값을 리턴하지 않으면, 컴파일 에러를 발생시킨다.

어떻게 하면 타입을 잘 작성할 수 있는지 알아보자!  

### <span style="color:#febc68;font-weight:bold">Structural Type System</span>
타입스크립트는 Structural Type System을 따르고 있다!  
Structural Type System에서는 구조가 같으면 같은 타입이다!
```javascript
    interface a{
        name: string;
        age: number;
        speak: string
    }
    type b = {
        name: string;
        age: number;
        speak(): string
    }
    //a 와 b는 구조가 같기 때문에 같다.
```
### <span style="color:#febc68;font-weight:bold">Nominal Type System</span>
Structural Type System과 대비되는 Nominal Type System이 있고, 이를 사용하는 대표적인 언어는 C언어,Java 가 있다.  
Nominal Type System에서는 구조가 같아도 이름이 다르면, 다른 타입이다!  
