---
title: TypeScript(2)
categories: [TIL, TypeScript]
tags: [TypeScript] # TAG names should always be lowercase
---

# 내일배움캠프 LGLG!

## 주특기 플러스 주차 - TypeScript

### TypeScript 고급 타입 활용하기

1) Partial\<T> 타입
- 타입 T의 모든 속성을 선택적으로 만든다.
- 기존 타입을 `일부 속성만 제공하는 객체`를 쉽게 생성할 수 있다.
```ts
interface Person {
  name: string;
  age: number;
}

const updatePerson = (person: Person, fields: Partial<Person>): Person => {
  return { ...person, ...fields };
};

const person: Person = { name: "Spartan", age: 30 };
const changedPerson = updatePerson(person, { age: 31 });
```

2) Required\<T> 타입
- 타입 T의 모든 속성을 필수적으로 만든다.
- T 타입 객체에 정의된 `모든 속성이 반드시 전부 제공`이 되는 객체를 생성해야 할 때 쓰인다. 
```ts
interface Person {
  name: string;
  age: number;
  address?: string;
}
```
- `address?`는 선택적 속성이다.
- 있어도 되고 없어도 됨
- But, address를 필수적으로 받아야 하는 제약사항을 만들 수 있음
```ts
type RequiredPerson = Required<Person>;
```
- 위처럼 Required\<T> 타입을 통해 선언하면 address 입력도 필수가 된다.

3) Readonly\<T> 타입
- 타입 T의 모든 속성을 읽기 전용(read-only)으로 만든다.
- readonly 타입의 속성들로 구성된 객체가 아니어도 완전한 불변 객체로 취급할 수 있음
```ts
interface DatabaseConfig {
  host: string;
  readonly port: number; 
  // 인터페이스에서도 readonly 타입 사용 가능
}

const mutableConfig: DatabaseConfig = {
  host: "localhost",
  port: 3306,
};

const immutableConfig: Readonly<DatabaseConfig> = {
  host: "localhost",
  port: 3306,
};

mutableConfig.host = "somewhere";
immutableConfig.host = "somewhere"; // 오류
```
4) Pick\<T, K> 타입
- 타입 T에서 `K 속성들만 선택하여 새로운 타입`을 만든다.
```ts
interface Person {
  name: string;
  age: number;
  address: string;
}

type SubsetPerson = Pick<Person, "name" | "age">;

const person: SubsetPerson = { name: "Spartan", age: 30 };
```
- SubsetPerson은 Person이라는 인터페이스에서 name, age 속성만 선택해서 구성된 새로운 타입이다.

5) Omit\<T, K> 타입
- 타입 T에서 K 속성들만 제외한 새로운 타입을 만든다.
- Pick\<T, K> 유틸리티 타입과는 반대의 동작
- 이를 통해 기존 타입에서 특정 속성을 제거한 새로운 타입을 쉽게 생성할 수 있다.
```ts
interface Person {
  name: string;
  age: number;
  address: string;
}

type SubsetPerson = Omit<Person, "address">;

const person: SubsetPerson = { name: "Alice", age: 30 };
```
- SubsetPerson 타입은 Person 타입에서 `address` 속성만 제외한 새로운 타입이다.

### 클래스
- 객체 지향 프로그래밍(OOP)의 핵심 구성 요소 중 하나
- 객체를 만들기 위한 틀(template)

#### 클래스의 구성 요소
- 같은 종류의 객체들이 공통으로 가지는 속성(attribute)과 메서드(method)를 정의한다.
  > 속성은 `객체의 성질`을 결정하는 것<br>
  > 매서드는 `객체의 성질을 변화`시키거나 `객체에서 제공하는 기능들을 사용`하는 창구

### 객체
- 클래스를 기반으로 생성되며 클래스의 인스턴스(instance)라고도 한다.

### 클래스 및 객체 정의 방법
- TypeScript에서 클래스를 정의하려면 `class` 키워드를 사용하면 된다.
- 클래스의 속성과 메서드를 정의하고, `new` 키워드를 사용하여 객체를 생성할 수 있다.

```ts
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  sayHello() {
    console.log(`안녕하세요! 제 이름은 ${this.name}이고, 나이는 ${this.age}살입니다.`);
  }
}

const person = new Person('Spartan', 30);
person.sayHello();
```

### 생성자(constructor)
- 클래스의 인스턴스를 생성하고 초기화하는데 사용되는 특별한 메서드
- 클래스 내에서 `constructor`라는 이름으로 정의
- 인스턴스를 생성할 때 자동으로 호출
- 클래스 내에 오직 하나만 존재할 수 있음

### 접근 제한자
- 클래스에서는 속성과 메서드에 접근 제한자를 사용해 접근을 제한할 수 있다.
- TypeScript에서는 다음의 접근 제한자들을 제공
  > `public`
  >> `클래스 외부에서도 접근이 가능한 접근 제한자`<br>
  >> 접근 제한자가 선언되지 않았을 때의 기본 접근 제한자<br>
  >> 보통은 클래스의 함수 중 민감하지 않은 객체 정보를 열람할 때나 누구나 해당 클래스의 특정 기능을 사용해야 할 때 많이 쓰임

  > `private`
  >> `클래스 내부에서만 접근이 가능한 접근 제한자`<br>
  >> 보통은 클래스의 속성은 대부분 private으로 접근 제한자를 설정<br>
  >> 클래스의 속성을 보거나 편집하고 싶다면 별도의 getter/setter 메서드를 준비해놓는 것이 관례이다.

  > `protected`
  >> `클래스 내부와 해당 클레스를 상속받은 자식 클래스에서만 접근`이 가능한 접근제한자

    ```ts
    class Person {
    private name: string;
    private age: number;

    constructor(name: string, age: number) {
      this.name = name;
      this.age = age;
    }

    public sayHello() {
      console.log(`안녕하세요! 제 이름은 ${this.name}이고, 나이는 ${this.age}살입니다.`);
      }
  }
    ```

### 상속(inheritance)
- 객체 지향 프로그래밍에서 클래스 간의 관계를 정의하는 중요한 개념
- `기존 클래스의 속성과 메서드를 물려받아` 새로운 클래스를 정의할 수 있음
- 똑같은 코드를 계속 반복적으로 작성할 필요 없음
- 상속을 구현하려면 `extends` 키워드를 사용

#### 서브타입의 정의
> 두 개의 타입 A와 B가 있고 B가 A의 서브타입이면 A가 필요한 곳에는 어디든 B를 안전하게 사용할 수 있다.*

#### 슈퍼타입의 정의
> 두 개의 타입 A와 B가 있고 B가 A의 슈퍼타입이면 B가 필요한 곳에는 어디든 A를 안전하게 사용할 수 있다.

### upcasting
- `서브타입 → 슈퍼타입으로 변환`을 하는 것
- 타입 변환은 암시적으로 이루어져 별도의 타입 변환 구문이 필요없음
  > 타입스크립트가 자동으로 해줌
- 서브타입 객체를 슈퍼타입 객체로 다루면 유연하게 활용할 수 있기 때문에 필요함

### downcasting
- `슈퍼타입 → 서브타입으로 변환`을 하는 것
- `as` 키워드로 `명시적으로 타입 변환`을 해줘야 함

### 추상 클래스
- 인스턴스화를 할 수 없는 클래스
- 상속을 통해 자식 클래스에서 메서드를 제각각 구현하도록 강제를 하는 용도
- 최소한의 기본 메서드는 정의를 할 수 있으나 `핵심 기능의 구현은 전부 자식 클래스에게 위임`한다.

#### 추상 클래스 사용 방법
- 추상 클래스 및 추상 함수는 `abstract` 키워드를 사용하여 정의
- 1개 이상의 추상 함수가 있는 것이 일반적이다.

```ts
abstract class Shape {
  abstract getArea(): number; // 추상 함수 정의!!!

  printArea() {
    console.log(`도형 넓이: ${this.getArea()}`);
  }
}

class Circle extends Shape {
  radius: number;

  constructor(radius: number) {
    super();
    this.radius = radius;
  }

  getArea(): number { // 원의 넓이를 구하는 공식은 파이 X 반지름 X 반지름
    return Math.PI * this.radius * this.radius;
  }
}

class Rectangle extends Shape {
  width: number;
  height: number;

  constructor(width: number, height: number) {
    super();
    this.width = width;
    this.height = height;
  }

  getArea(): number { // 사각형의 넓이를 구하는 공식은 가로 X 세로
    return this.width * this.height;
  }
}

const circle = new Circle(5);
circle.printArea();

const rectangle = new Rectangle(4, 6);
rectangle.printArea();
```

### 인터페이스
- TypeScript에서 객체의 타입을 정의하는데 사용
- 객체가 가져야 하는 속성과 메서드를 정의
- 인터페이스를 구현한 객체는 인터페이스를 반드시 준수해야 한다.
  > 규약과 같아서 어길 수가 없음
- 인터페이스를 사용하면 코드의 안정성을 높이고 유지 보수성을 향상시킬 수 있음

#### 추상 클래스와 인터페이스의 차이
- 구현부 제공 여부
  > 추상 클래스 : 클래스의 기본 구현을 제공<br>
  > 인터페이스 : 객체의 구조만을 정의하고 기분 구현을 제공하지 않음

- 상속 매커니즘
  > 추상 클래스 : 단일 상속만 지원<br>
  > 인터페이스 : 다중 상속 지원 / 하나의 클래스는 여러 인터페이스 구현 가능

- 구현 매커니즘
  > 추상 클래스 : 상속받은 자식 클래스는 반드시 추상 함수를 구현해야 함<br>
  > 인터페이스 : 인터페이스에 정의된 모든 메서드를 전부 구현해야 함
  
 #### * 기본 구현을 제공하고 상속을 통해 확장하는데 초점을 맞춘다 -> `추상 클래스`
 #### * 객체가 완벽하게 특정 구조를 준수하도록 강제하고 싶다 -> `인터페이스`

### 객체 지향 설계 원칙 (S.O.L.I.D)

#### S (SRP 단일 책임 원칙)
- 클래스는 `하나의 책임`만 가져야 한다는 기본적인 원칙
- 5개의 설계 원칙 중 `가장 기본적이고 중요한 원칙`

잘못된 사례)
```ts
class UserService {
  constructor(private db: Database) {}

  getUser(id: number): User {
    // 사용자 조회 로직
    return this.db.findUser(id);
  }

  saveUser(user: User): void {
    // 사용자 저장 로직
    this.db.saveUser(user);
  }

  sendWelcomeEmail(user: User): void {
    // 갑분 이메일 전송 로직이 여기 왜?
    const emailService = new EmailService();
    emailService.sendWelcomeEmail(user);
  }
}
```

올바른 사례)
```ts
class UserService {
  constructor(private db: Database) {}

  getUser(id: number): User {
    // 사용자 조회 로직
    return this.db.findUser(id);
  }

  saveUser(user: User): void {
    // 사용자 저장 로직
    this.db.saveUser(user);
  }
}

class EmailService {
  // 이메일 관련된 기능은 이메일 서비스에서 총괄하는게 맞습니다.
  // 다른 서비스에서 이메일 관련된 기능을 쓴다는 것은 영역을 침범하는 것이에요!
  sendWelcomeEmail(user: User): void {
    // 이메일 전송 로직
    console.log(`Sending welcome email to ${user.email}`);
  }
}
```

#### O (OCP 개방 폐쇄 원칙)
- 클래스는 확장에 대해서는 열려 있어야 하고 수정에 대해서는 닫혀 있어야 한다는 원칙
- 클래스의 기존 코드를 변경하지 않고도 기능을 확장할 수 있어야 함
- `인터페이스`나 `상속`을 통해서 이를 해결할 수 있음

#### L (LSP 리스코프 치환 원칙)
- `서브타입은 기반이 되는 슈퍼타입을 대체`할 수 있어야 한다는 원칙
- 자식 클래스는 부모 클래스의 기능을 수정하지 않고도 부모 클래스와 호환되어야 함
- 논리적으로 엄격하게 관계가 정립이 되어야 함

잘못된 사례)
```ts
class Bird {
  fly(): void {
    console.log("펄럭펄럭~");
  }
}

class Penguin extends Bird {
  // 펭귄은 날 수 없다!!
}
```

올바른 사례)
```ts
abstract class Bird {
  abstract move(): void;
}

class FlyingBird extends Bird {
  move() {
    console.log("펄럭펄럭~");
  }
}

class NonFlyingBird extends Bird {
   move() {
    console.log("뚜벅뚜벅!");
  }
}

class Penguin extends NonFlyingBird {} 
```

#### I (ISP 인터페이스 분리 원칙)
- 클래스는 자신이 사용하지 않는 인터페이스의 영향을 받지 않아야 함
- 해당 클래스에게 무의미한 메소드의 구현을 막자는 의미이다.
- 인터페이스를 너무 크게 정의하기보단 필요한 만큼만 정의하고 클래스는 입맛에 맞게 필요한 인터페이스들을 구현하도록 유도한다.

#### D (DIP 의존성 역전 원칙)
- Java의 Spring 프레임워크나 Node.js의 Nest.js 프레임워크와 같이 웹 서버 프레임워크 내에서 많이 나오는 원칙
- 하위 수준 모듈(구현 클래스)보다 상위 수준 모듈(인터페이스)에 의존을 해야한다는 의미

예시)
```ts
interface MyStorage {
  save(data: string): void;
}

class MyLocalStorage implements MyStorage {
  save(data: string): void {
    console.log(`로컬에 저장: ${data}`);
  }
}

class MyCloudStorage implements MyStorage {
  save(data: string): void {
    console.log(`클라우드에 저장: ${data}`);
  }
}

class Database {
  // 상위 수준 모듈인 MyStorage 타입을 의존! 
  // 여기서 MyLocalStorage, MyCloudStorage 같은 하위 수준 모듈에 의존하지 않는게 핵심!
  constructor(private storage: MyStorage) {}

  saveData(data: string): void {
    this.storage.save(data);
  }
}

const myLocalStorage = new MyLocalStorage();
const myCloudStorage = new MyCloudStorage();

const myLocalDatabase = new Database(myLocalStorage);
const myCloudDatabase = new Database(myCloudStorage);

myLocalDatabase.saveData("로컬 데이터");
myCloudDatabase.saveData("클라우드 데이터");
```