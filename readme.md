# Vue.js란?

웹페이지 화면을 개발하기 위한 Frontend 프레임워크이다.
기존 웹 개발자 뿐 아니라 HTML, CSS, Javascript 기초만 알아도 개발하기 쉬운 Frontend 프레임워크이다.

## 창시자

에반 유(Evan You)

## 설명

뷰 코어 라이브러리는 화면단 데이터 표현에 관한 기능들을 중점적으로 지원하지만 프레임워크의 기능인 라우터, 상태 관리, 테스팅 등을 쉽게 결합할수 있는 형태로도 제공됩ㄴ다. 즉. 라이브러리 역할 뿐 아니라 프레임워크 역할도 할수있다.

## 장점

1. 배우기가 쉽다.
1. 리액트와 앵귤러에 비해 성능이 우수하고 빠르다.
   - Vue 제작팀에서 리액트와 앵귤러를 가지고 같은 테스트 케이스에서 성능을 비교한 결과 vue가 가장 빨랐다.
1. 리액트의 장점과 앵귤러의 장점을 갖고 있다.
   - 앵귤러의 데이터 바인딩 특성
   - 리액트의 가상 돔 기반 렌더링 특징

## Vue.js 특징

### UI 화면단 라이브러리

MVVM(Model, View, ViewModel) 패턴의 뷰 모델에 해당하느 화면단 라이브러리 이다.

### 용어 설명

- 뷰(View) : 사용자에게 보이는 화면
- 돔(Dom) : HTML 문서에 들어가는 요소(태그, 클래스, 속성 등)의 정보를 담고있는 데이터 트리
- 돔 리스너 (Dom Listener) :돔의 변경 내역에 대해 즉각적으로 반응하여 특정 로직을 수행하는 장치
- 모델(Model) : 데이터를 담는 용기. 보통은 서버에서 가져온 데이터를 자바스크립트 객체 형태로 저장
- 데이터 바인딩 (Data Binding) : 뷰(View)에 표시되는 내용과 모델의 데이터를 동기화
- 뷰 모델(View Model) : 뷰와 모델의 중간 영역. 돔 리스너와 데이터 바인딩을 제공하는 영역

### 컴포넌트 기반 프레임워크

컴포넌트란 마치 레고 블록과 같습니다. 레고 블록을 잘 조합해서 쌓으면 원하는 모형을 만들수 있듯이 뷰의 컴포넌트를 조합하여 화면을 구성할수있습니다.

## 기본 Vue.js 코드

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vue Sample</title>
  </head>
  <body>
    <div id="app">
      {{message}}
      <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.min.js"></script>
      <script>
        // 인스턴스
        new Vue({
          el: "#app", // el 속성
          data: {
            // 데이터 속성
            message: "Hello Vue.js!",
            // template : 화면에 표시할 HTML, CSS등의 마크업 요소를 정의하는 속성, 뷰의 데이터 및 기타 속성 들도 함께 화면에 그릴수 있으며 05장 뷰 템플리셍서 자세히 설명합니다.
            // methods : 화면 로직 제어와 관계된 메서드를 정의하는 속성, 마우스 클릭 이벤트 처리와 같이 화면의 전반적인 이벤트와 화면 동작과 관련된 로직을 추가할 수있습니다.
            // created : 뷰 인스턴스가 생성되자마자 실행할 로직을 정의 할 수 있는 속성, 뷰 인스턴스 라이프 사이클 부분에서 추가로 설명합니다.
          },
        });
      </script>
    </div>
  </body>
</html>

```

### 뷰 인스턴스 유효 범위

뷰 인스턴스를 생성하면 HTML의 특정 범위 안에서만 옵션 속성들이 적용되어 나타납니다. 이를 인스턴스 유효범위라고 합니다.
지역 컴포넌트와 전역 컴포넌트 차이를 알기 위해 필요한 개념입니다.

### 뷰 인스턴스 속성 적용 과정

1.  뷰 라이브러리 파일 로딩
2.  인스턴스 객체 생성(옵션 속성 포함)
3.  특정 화면 요소에 인스턴스를 붙임
4.  인스턴스 내용ㅇ이 화면 요소로 변환
5.  변환된 화면 요소를 사용자가 최종 확인

### 뷰 인스턴스 라이프 사이클 속성

created, beforeCreate, beforeMount, mounted 등 인스턴스의 생성, 변경, 소멸과 관련되어 총 8개가 존재 한다.

### 뷰 라이프 사이클 다이어 그램 (1.생성 -> 2.부착 -> 3.갱신 -> 4.소멸)

1. 생성단계 : -> 인스턴스 생성
2. 부착단계 : -> 이벤트 및 라이프 사이클 초기화 -> beforeCreate -> 화면에 반응성 주입 -> created -> el, template송성 확인 -> template 속성 내용을 render()로 변환 -> beforeMount -> $el 생성후 디 속성값을 대입 -> mounted -> 인스턴스를 화면에 부착
3. 갱신단계 : -> 인스턴스의 데이터 변경 -> beforeUpdate -> 화면 재 렌더링 및 데이터 갱신 -> upload -> 인스턴스 내용 갱신
4. 소멸단계 : -> 인스턴스 접근 가능 -> beforeDestroy -> 컴포넌트, 인스턴스, 디렉티브 등 모두 해제 -> destroyed -> 인스턴스 소멸

### 라이플 사이클 속성

- beforeCreate
  - 인스턴스 생성후 최초 실행
  - data, methods 속성 아직 정의 X
  - 돔 접근 X
- created
  - data, methods정의 (this.data or this.fetchData() 등과 같은 로직을 이용하여 data, methods에 접근 하여 로직 실행 가능)
  - 화면에 부착 전 이기 때문에 templates는 접근 X
  - 서버에 데이터를 요청하여 받아 오는 로직 수행하기 적합하다.
- beforeMount
  - template 속성에 지정한 마크업 속성을 render()함수로 변환한 후 el 속성에 지정한 화면 요소에 인스턴스를 부착하기 전에 호출되는 단계
  - render() 함수가 호출되기 직전의 로직을 추가 하기 좋다.
- mounted
  - el 속성에서 지정한 화면 요소에 인스턴스 부착 하면 호출
  - template속성에 정의한 화면 요소에 접근 할수 있어 화면 요소를 제어 하는 로직을 수행하기 좋다.
  - 단 돔에 인스턴스가 부착 되자 마자 호출되기 때문에 하위 컴포넌트나 외부 라이브러리에 의해 추가된 화면 요소들이 최종 HTML코드로 변환되는 시점과 다를수있다.
- beforeUpdate
  - el 속성에서 지정한 화면 요소에 인스턴스가 부착되고 나면 인스턴스에 정의한 속성들이 화면에 치환됩니다.
  - 치환된 값은 뷰의 반응성을 제공하기 위해 $watch속성으로 감시 한다. 이를 데이터 관찰이라 한다.
  - 데이터 관찰시 데이터가 변경되면 가상 돔으로 화면을 다시 그리기 전에 호출되는 단계이며, 변경 예정인 새 데이터에 접근 할 수있어 변경 예정 데이터의 값과 관련된 로직을 미리 넣을수있다. 만약 여기에 값을 변경하는 로직을 넣더라도 화면이 다시 그려지지 않는다.
- updated
  - 데이터가 변경되고 나서 가상 돔으로 다시 화면을 그리고 나면 실행되는 단계이다.
  - 데이터 변경으로 인한 화면 요소 변경 까지 완료된 시점 이므로, 데이터 변경 후 화면 요소 제어와 관련된 로직을 추가하기 좋은 단계이다.
  - 이 단계에서 데이터를 변경하면 무한 루프에 빠질수있기때문에 변경시 Computed, watch와 같은 속성을 사용해야한다.
    - 따라서 데이터 값을 갱신하는 로직은 가급적이면 beforeUpdate에 추가 하고, updated에서는 변경 데이터의 화면 요소와 관련된 로직을 추가 하는것이좋다.
- beforeDestroy
  - 뷰 인스턴스가 파괴되기 직전에 호출되는 단계
  - 아직 인스턴스에 접근 할수있다.
  - 따라서 뷰 인스턴스의 데이터를 삭제 하기 좋은 단계
- destroyed
  - 뷰 인스턴스가 파괴되고 나서 호출되는 단계
  - 뷰 인스턴스에 정의한 모든 속성이 제거되고 하위에 선언한 인스턴스들 또한 모두 파괴 된다.

## 컴포넌트란?

조합하여 화면을 구성할 수 있는 블록(화면의 특정영역)을 의미한다.

### 특징

- 컴퓨넌트를 활용하면 화면을 빠르게 구조화 하여 일괄적인 패턴으로 개발 할 수 있다.
- 쪼개서 사용하므로 재사용이 쉽다.
- 남이 작성한 코드를 직관적으로 이해 할 수있다.

## 컴포넌트를 이해 하기 위하 예제 구조 설명

뷰 에서는 웹화면을 구성할 때 흔히 사용하는 네비게이션바, 테이블, 리스트, 인풋 박스 등과 같은 화면 구성 요소들을 잘게 쪼개어 컴포넌트로 관리 합니다.

Tree 형식으로 구조화 되어 있다.

- Root
  - Header
  - Content
    - Aside
    - List
  - Footer

## 컴포넌트 등록

- 전역(global))
  - 여러 인스턴스에서 공통으로 사용한다.
  - 뷰로 접근 가능한 모든 범위에서 사용할수있다.
- 지역(local)
  - 특정 인스턴스에서만 유효한 범위를 갖는다.

### 1. 전역 컴포넌트 등록

전역 컴포넌트는 뷰 라이브러리를 로딩하고 나면 접근 가능한 Vue변수를 이용하여 등록한다.
전역 컴포넌트를 모든 인스턴스에 등록하려면 Vue생성자에서 .Component()를 호출 하여 수행하면된다.

```html
Vue.compoent("컴포넌트 이름", { // 컴포넌트 내용 });
```

1. 컴포넌트 이름
   - template 속성에서 사용할 HTML사용자 정의 태그(custom tag)이름을의 이름을 의미한다.
   - 태그 이름의 명명 규칙은 HTML 사용자 정의 태그 스펙에서 강제 하는 '모든 소문자', '케밥 기법'을 따르지 않아도 된다.
     - 케밥 기법 : 변수가 단어의 조합으로 이루어져 있을때, 단어와 단어 사이를 -로 잇는 변수 명명 방식
   - 실제 화면의 HTML 요소로 변환 될때 표시될 속성들을 컴포넌트 내용에 작성한다.
     - 컴포넌트 내용에는 template,data, methods등 인스턴스 옵션 속성을 정의 할수있다.

#### 예제

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vue life Cycle</title>
  </head>
  <body>
    <div id="app">
      <button>컴포넌트 등록</button>
      <!-- 전역 컴포넌트 표시 -->
      <my-component></my-component>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.5.2/dist/vue.js"></script>
    <script>
      // 전역 컴포넌트 등록
      Vue.component("my-component", {
        template: "<div>전역 컴포넌트가 등록되었습니다.</div>",
      });
      new Vue({
        el: "#app",
      });
    </script>
  </body>
</html>
```

#### 컴포넌트 처리 과정

1. 뷰 라이브러리 파일 로딩
2. 뷰 생성자로 컴포넌트 등록
   - Vue.component()
3. 인스턴스 객체 생성(옵션 속성 포함)
4. 특정 화면 요소에 인스턴스 부착
5. 인스턴스 내용변환
   - 등록된 컴포넌트 내용도 변환
   - my-component -> div로 변환 한다.
6. 변환된 화면 요소를 사용자가 최종확인

### 2. 지역 컴포넌트 등록

지역 컴포넌트 등록은 전역 컴포넌트 등록과는 다르게 인스턴스에 components속성을 추가하고 등록할 컴포넌트 이름과 내용을 정의 하면된다.

```html
new Vue({ componets: { '컴포넌트 이름': 컴포넌트 내용 } })
```

#### 예

```html
<body>
  <div id="app">
    <button>컴포넌트 등록</button>
    <!-- 전역 컴포넌트 표시 -->
    <my-local-component></my-local-component>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.2/dist/vue.js"></script>
  <script>
    var cmp = {
      // 컴포넌트 내용
      template: "<div>지역 컴포넌트가 등록되었습니다.!</div>",
    };
    new Vue({
      el: "#app",
      components: {
        "my-local-component": cmp,
      },
    });
  </script>
</body>
```

### 지역 컴포넌트와 전역 컴포넌트 차이

```html
<body>
  <div id="app">
    <h3>첫 번째 인스턴스 영역</h3>
    <my-global-component></my-global-component>
    <my-local-component></my-local-component>
  </div>
  <div id="app2">
    <h3>두 번째 인스턴스 영역</h3>
    <my-global-component></my-global-component>
    <my-local-component></my-local-component>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.5.2/dist/vue.js"></script>
  <script>
    // 전역 컴포넌트 등록
    Vue.component("my-global-component", {
      template: "<div>전역 컴포넌트 입니다.</div>",
    });

    // 지역 컴포넌트 등록
    var cmp = {
      template: "<div>지역 컴포넌트입니다.</div>",
    };

    // 첫번째 인스턴스
    new Vue({
      el: "#app",
      // 지역 컴포넌트 등록
      components: {
        "my-local-component": cmp,
      },
    });

    // 두번째 인스턴스
    new Vue({
      el: "#app2",
    });
  </script>
</body>
```
