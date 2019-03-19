# 뱅크샐러드 레퍼런스

2:00~ 시작

원래회사이름 : 점심콩부터시작

두달에 한번씩 진행하는 행사

다음은 5월



#### 세션

1Track : webTrack

2Track : mobileTrack



---

---

## webTrack

## 미리 맛보는 Morden Javascript

발표자 : 이동근

많이쓰면 경고 / 잘쓰면 조언 / 금융 리치서? / 연금기능담당



### 01. ECMAScript

#### 표준을 누가 만드는지, 어떻게 이루어지는지

탄생 원인 : javascript는 동적 움직임을 위해 탄생되었고, 시간이 지나서  브라우저 별 스크립트가 만들어짐

정의 : Javascript가 다양한 웹브라우저에서 공통적으로 작동하기 위한 표준규격



#### poroposal 단계

Stage0 : strawman (허수아비)

Stage1 :proposal

Stage2 : draft

Stage3 :candidate (후보자)

Stage4 : finished



##### Optional Chaining

- 말 그대로 특정 값에 대한 참조에 대해서 값이 존재하지 않을 때 선택적으로 체이닝할 수 있는 문법

  (ex. C# - conditional operator, swift - optional changing, coffee script - existsntial operator)

- null check 가능 / 중단없이 값이 나오거나 undefined 표출

- ?.을 사용하여 프로퍼티가 존재하는 유무를 체크

```java
const obj = {
    profile: {}
};

if(obj.hasOwnProperty('profile')){
    obj.profile.name = 'laplace';
}

console.log(obj.profile.name); // laplace
```

만약 여기서 profile이 없는 상태에서 name을 접근하면 오류남

-> 프로퍼티 존재유무를 체크하는 방어적 로직을 넣어야함

```javascript
a?.b;                          // a가 null/undefined라면 undefined, 아니면 a.b를 반환한다.
a == null ? undefined : a.b;

a?.[x];                        // a가 null/undefined라면 undefined, 아니면 a[x]를 반환한다.
a == null ? undefined : a[x];

a?.b();                        // a가 null/undefined라면 undefined
a == null ? undefined : a.b(); // a.b가 함수가 아니라면 TypeError를 던진다.
                               // 위 경우가 아니라면 a.b를 실행

a?.();                         // a가 null/undefined라면 undefined
a == null ? undefined : a();   // a가 null/undefined, function이 아닌 경우 TypeError를 던진다.
                               // 위 경우에 해당하지 않을 경우 a를 실행
```



#### proposal에서 발견한 것들

##### Class field

-  클래스 컴포넌트를 간편하게 사용 ㅇㅇ

-  private 사용가능

-  현재 Stage3 단계
- Hashtag(#)를 붙여서 private를 표현

```javascript
class Point {
  #x;
  #y;

  constructor(x, y) {
    this.#x = x;
    this.#y = y;
  }

  equals(point) {
    return this.#x === point.#x && this.#y === point.#y;
  }
}
```



##### React Hook

- class없이 state를 사용할 수 있는 새로운 기능

```javascript
function Example(props) {
  return <div />;
}
```

참고 https://velog.io/@vies00/React-Hooks



##### Dynamic import

- 모듈 필요할때 부를 수 있는 거 (sentry?는 에러안나면 필요 없는데..)

- 속도 향샹

- 실제코드를 부를 수 있음
- import할 module명을 넣음

```javascript
import('./ImportClass.js');
```

```javascript
export default class ImportClass {
    constructor() {
        console.log('import!');
    }
}
```

```javascript
import('./ImportClass').then(importClassJs => {
    new importClassJs.default();
});
```

importClass.js 스크립트에서 default가 class에 선언되어있음

importClassJS.default()로 class객체 생성

(-> default로 생성하지 않았다면 importClassJS.ImportClass()로 생성함)

참고 https://smilerici.tistory.com/38



##### Array.Flat() & Array.FlatMap()

-> Array 중첩을 해결



##### TryCatch

-> error 생략 가능



##### String.trimStart() & String.trimEnd()



proposal 읽어보고 괜춘하면 써보자리(git ㄲ)~~



---

#### 질문

1. 사람들끼리 설정 : project 진행할때 기간 선정해서 이만큼햇을때 이렇게되겟다 

2. proposal에서 finish 단계로 가면 결정권자는 누가되는거? Apple, google, sony, etc

3. 회사장점 : 자기주장 가능(ex. 내가 써보고싶을때 사람들이 긍정적으로 반응해줌)

4. proposal에서 끝까지 승인이 안돼면 기술부채가 일어나는데 어캄? 표준의 거의 픽셀이 되거나 없어져도 문제가 안될것들을 체크리스트로 가지고 있고, 인지하고있다.
5. 새로운걸 진행하는 프로세스 : 아이디어내고 승인나면 각자 테스크 만듬 / 기간 산정하고 스크립트함





---

---



## 파이썬맛 레시피

발표자 : 정겨울

파트 : 백엔드 파이썬



### 주제

01 어떤 환경에서 파이썬사용했는가

02 패턴

03 어떻게 사용하고 있는가



#### 린학습? (Lean?)

빠른 개선과 배포



네트워크 io가 많은 mas 환경



#### 이벤트 루프 비동기 방식

1. 어떤 방식이든 비동기면 원하는 성능 달성 가능
2. 가장 일반적인 익숙한패턴
3. 언어 레벨에서 나이스한 문법 제공
4. 특정 파이선 라이브러리 어쩌구

파이썬 3.7이상 사용중



### 02 파이썬을 사용하는 패턴



#### Sonic

비동기 웹프레임워크 사용



#### Aiohttp & sanic 장점 

빠름 

간결한문법

확장된 기능제공 

잘관리됨



#### sanic라우팅 장점

1. 중첩 가능하고 추상화된 블루프린트

2. 글로벨 세션과 리스너

3. 컨피그 팩토리 패턴



#### 클린아키텍쳐 개념 도입

1. 도메인 중심으로 개발 가능 

사용자 중심으로 생각하고 개발하려고

2. 공통된 구조를 통해 유지보수 쉬움

ex) 다른 서비스나 db에서 갚을 꺼내오는 로직

data의 repository?

3. Entity + dataclass



#### Docker 컨테이너

장점

1. 멀티 스테이지 빌드



### TEST

#### pytest라이브러리 사용

Unittest + nose < pytest

모든 unities 코드는 pytest 가능

간결하고 깔끔한 테스트 코드

읽기쉬운 에러리포트

fixture와 플러그인 (에러로직에만 집중할 수 있도록)



#### db테스트

서비스로직 안건들이고 값만 가져오는걸 만듬



#### 외부 API 테스팅

외부 api는 값을 받아오는 것 보단 로직에 맞게 보내지는걸 확인?



#### COVERAGE

Purest-cov로 커버리지 리포트 생성

커버리는 목표가 아닌 상태



#### 린트와 스타일

isort

git hook을 통한 테스트 자동화

git hook을 통한 사전테스트



### 03 함께하는개발

협업

코드 컨벤션

Rainist / styleGuide -> 전원 합의를 거친 코드 컨벤션

템플릿으로 관리



### gitHub

Issu / pr 템플릿

Issu_template.md

-> 맥락파악 레거시화 의사소통비용감서

이슈 라벨링 (타입별 구분)

코드리뷰는 500줄 이내로



---

#### 질문

1. 지라를통해 이슈관리
2. 디비는 몽고디비 RDB : mysql? 

RDB (Relation Database) 

- 관계형 데이터모델에 기초
- 모든 데이터를 2차원의 테이블 형태로 표현

1. 파이썬 버전 호환 괜춘했는지?

마이그레이션에 대한 이슈는 없었음

4. pytest & debuging 장단점

pytest사용 이유 : 로직이 기대한 결과값을 내뱉고 있는지 확인

디버깅 사용 이유 : 디버깅을 수행하면서 수정할내용찾아
