---
layout: post
title: Typescript - 기본 타입 Object
date: 2022-09-12 17:21:07 +0900
category: TypeScript
---

## <span style="color:#97cab3;font-weight:bold">Primitive Type</span>
Primitive Type은 Object와 Reperence type이 아닌 실제 데이터를 저장하는 타입을 말한다.  
이에 해당하는 타입으로는 boolean, number, string, symbol, null, undefined가 있다.  
이 타입은 literal(문자 그대로)값으로 Primitive 타입의 서브타입을 나타낼수 있다.

주의할 점은 Primitive type은 모두 소문자로 작성해야한다는 것이다.  
또한 Number, String, Boolean을 이용하여 Reference Type 중 하나인 래퍼객체(Wrapper Object)를 만들 수 있으나, TypeScript에서는 권장하지 않는다.

### <span style="color:#febc68;font-weight:bold">1.boolean</span>

```javascript
    let isDone: boolean = false;
    isDone = true;
    console.log(typeof isDone)
    // 출력값 boolean
```
### <span style="color:#febc68;font-weight:bold">2.number</span>
```javascript
    //10진수
    let decimal: number = 6;
    //16진수
    let hex: number = 0xf00d;
    //2진수
    let binary: number = 0b1010;
    //8진수
    let octal: number = 0o744;

    let Nan: number = NaN;

    let underscoreNum: number = 1_000_000;
```

### <span style="color:#febc68;font-weight:bold">3.string</span>
javascript와 같이 큰따옴표나 작은 따옴표를 사용한다.
```javascript
    // string 
    let name: string = "joj";

    // templete string
    let name: string = "joj"
    let age:number = "30"

    let sentence:string = `Hello, I'm ${name} and ${age} years old!`
```
### <span style="color:#febc68;font-weight:bold">4.symbol</span>
Symbol은 고유하고 변경할 수 없는 식별자를 생성하며, 한 번 생성하면 복사할 수 없다.
사용 목적은 객체의 고유한 프로퍼티 키를 만들기 위해 사용된다.
  
### <span style="color:#febc68;font-weight:bold">5.null, undefined</span>
void와 마찬가지로 자체만으로는 유용하지 않으며, 둘다 소문자만 존재한다.  
별도의 설정없이 사용할 때, number나 string 과 같은 다른 타입의 값으로 할당이 가능하다.  
자기 자신들에게만 할당하게 하기 위해서는 컴파일 옵션에서 아래의 옵션을 사용하면 된다.
 `--strictNullChecks'