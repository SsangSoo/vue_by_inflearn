# Vue framework Learning

뷰3 프레임워크를 학습하는 Repository입니다.

해당 Repository는 인프런의 짐코딩 - Vue3 완벽 마스터: 기초부터 실전까지 - "기본편" 의 강의를 수강하며 학습하는 레포입니다.

커리큘럼상 게시판 프로젝트가 진행된다고 합니다.
해당 게시판 프로젝트의 백엔드 서버는 추후에 개발과 구현해보려고합니다.

# IDE
JetBrain에서 제공하는 WebStrom을 이용합니다.


## 내용 정리

<details>
<summary>개발환경 구성</summary>
- 강의에서 소개하는 vsCode의 확장프로그램은 이미 WebStrom에서 모두 제공되는 기능이므로, 생략합니다. <br>
- 크롬 웹스토어에서 `vue devtools`를 검색하면 Vue.js devtools 2개가 나오는데, 이중 legacy는 Vue2를 가리킵니다. <br> 따라서 레거시가 아닌 Vue.js devtools를 설치합니다.
</details>



<details>
<summary>Vue란 무엇인가?</summary>

## Vue
User Interface 개발을 위한 자바스크립트 프레임워크입니다.

관련된 파일은 [vue3.html](./src/tmp/vue3.html), [javascript.html](./src/tmp/javascript.html) 입니다.

이 두 파일의 차이는 다음과 같습니다.
1. 선언적 렌더링(Declarative Rendering) : Vue는 템플릿 구문`{{ 데이터 }}`를 활용하여 데이터를 선언적으로 출력(렌더링)할 수 있도록 합니다.
 
2. 반응성(Reactivity) : Vue는 JavaScript 상태 변경을 자동으로 추적하고 변경이 발생하면 DOM을 효율적으로 업데이트합니다.

이를 활용하여 순수 자바스크립트를 이용하는 것보다 더욱 빠르게 애플리케이션을 제작할 수 있습니다.

### Vue의 바인딩

관련된 파일은 [quickly.html](./src/tmp/quickly.html)입니다.

v-bind 속성을 이용하여 script태그에서 선언한 message를 바인딩 시켜줍나다 .  <br>
그리고 message의 값이 변경되면, 자동으로 placeholder의 값도 변경됩니다.

참고로 vue.js devtools를 다운로드하고, 다음과 같이 사용할 수 있습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/0d4ac0f1-872a-4250-ae51-3a02e27ff335/image.png">
</div>

 <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/494205e7-11a3-4fce-b967-ad9470d31d08/image.png">
</div>

해당 값을 변경하면, 브라우저도 변경됩니다.

그리고 속성에서 `v-`라는 접두어가 붙은 특수 속성을 디렉티브(directive)라고 합니다.

### 이벤트 핸들링

관련된 파일은 [quickly.html](./src/tmp/quickly.html)입니다.

순수 html 태그 안에 `on`과 이벤트를 입력하면, 핸들링을 할 수 있는데,  <br>
Vue에선 `v-on`과 이벤트를 입력하여 핸들링을 할 수 있습니다.

reverseMessage와 관련된 코드입니다.

```
<!-- 이벤트 핸들링 -->
<button v-on:click="reverseMessage">click</button>
```

## 양방향 바인딩(v-model)

관련된 파일은 [quickly.html](./src/tmp/quickly.html)입니다.
username 과 관련된 코드입니다.

script에서 변경시엔, tag안의 값도 변경되어 나타납니다.  <br>
반면, 브라우저의 값을 변경하면, script 태그 안의 내용은 변경되지 않습니다.  <br>  <br>

왜냐하면, 단방향으로 바인딩되어 있기 때문인데요.  <br>
그래서 브라우저에서 값을 변경하면, 스크립트의 value도 변경될 수 있도록 **양방향 바인딩**을 해주어야 합니다.  <br> <br>

**양방향 바인딩**을 하기 위해 쓰는 것이 **v-model**입니다.  <br>
이 때 브라우저에서 값이 변경되면 스크립트의 value도 함께 변경됩니다.

```
{{ username }}
<!--    단방향 바인딩    <input type="text" v-bind:value="username" />-->
<!-- 양방향 바인딩 --> <input type="text" v-model="username" />
```


## 조건문
`v-if`라는 특수 속성(디렉티브)으로 제어할 수 있습니다.

관련된 파일은 [quickly.html](./src/tmp/quickly.html)입니다.

```
<p v-if="visible">보이나요?</p> <!-- 조건문 -->
<button type="button" v-on:click="visible = true">visible</button>
        
```


## 반복문
`v-for`로 배열에서 데이터를 가져와 아이템 목록을 표시하는데 사용할 수 있습니다.

관련된 파일은 [quickly.html](./src/tmp/quickly.html)입니다. 


```
<ul>
  <li v-for="item in items">{{item}}</li>
</ul>
```

</details>

<details>
<summary>컴포넌트 이해하기</summary>

**모듈** : 자바스크립트 코드를 재사용할 수 있도록 분리한 파일 <br><br>

**컴포넌트**                            <br>
- 뷰에서 UI를 재활용할 수 있도록 정의한 것   <br>                           
- 컴포넌트를 활용하면 자바스크립트 코드뿐만 아니라, HTML, CSS도 함께 캡슐화하여 재사용 가능. <br><br>

컴포넌트의 정의에든 두 가지 방법이 있습니다. <br><br>

하나는 **문자열 템플릿**, 하나는 **SFC(Single File Component)**가 있습니다. <br>

```
<script> 
    const BookComponent = {
        template : `
            <article class="book">
                <div class="book_subtitle">제목</div>
                <div class="book__title">HTML 강좌</div>
            </article>
        `,    
    };
    
    const app = Vue.createApp({});
    app.component("BookComponent",BookComponent);
    app.mount("#app");
</script>
```

위와 같이 component를 선언하고, <br>
등록했다면, <br>
사용만 하면 됩니다. <br><br>

사용은 body태그 안에 다음과 같이 추가만 해주면 됩니다.
<br>
```
<book-component></book-component>
```
<br>
그럼 해당 template 내의 구조가 만들어집니다.<br>


<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/cf18fbe6-38f7-4bf8-9fc3-81e8d5f421dc/image.png">
</div>

<br>

컴포넌트를 활용하면, 이처럼 단 몇 줄의 태그로 아래와 같은 UI를 만들 수 있습니다. <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/d98eaf54-a7df-4aa1-953e-60d9f58d01d9/image.png">
</div>

관련된 파일은 [여기](./src/learning-component/index.html)에 있습니다. <br><br>

그리고 위에 사진에 보시면 **Root 컴포넌트**가 존재함을 알 수 있는데, <br>
루트 컴포넌트는 처음 `Vue.craeteApp({})`으로 루트 컴포넌트를 처음에 생성할 때 괄호 안에 옵션을 전달하는데, <br>
그 옵션은 루트 컴포넌트를 생성할 때 사용하는 옵션입니다. <br><br>

그리고 이 태그들도 줄일 수 있습니다. <br>

```
const App = {
            template: `
            <app-header></app-header>
            <app-nav></app-nav>
            <app-view></app-view>
            `,
        }
///

app.component("App", App);
app.mount("#app");


//  HTML에 한 번에 한 줄로도 선언가능합니다.
<app></app>

```
<br>
지금까지의 방법은 **문자열 팀플릿**에 관한 내용입니다. <br>
이 방법은 계속 추가되는 내용이 있으면 코드가 길어지고, 불편해집니다. <br>

그래서 현업에서도 SFC 방식으로 개발을 진행하는데, <br>
SFC 방식으로는 **Vue CLI** 혹은 **Vite** 와 같은 빌드 도구가 필요합니다.

#### Vite 사용시

```
npm init -y
```

뷰도 npm으로 프로젝트를 관리할 것이기 때문에, cdn 방식이 아닌 npm으로 라이브러리를 설치해야 합니다.

```
npm install vue
```

vite 설치는 다음과 같습니다.

```
npm install vite
```

그리고 비트로 Vue.js 개발을 하려면 플러그인이 필요합니다. <br>

참고로 플러그인 [사이트는 바로 여기](https://github.com/vitejs/vite-plugin-vue/tree/main/packages/plugin-vue)입니다.

```
npm i @vitejs/plugin-vue
```

그리고 vite는 실행시 vite.config.js 파일을 참조합니다. <br><br>

다음으로 해당코드를 vite.config.js에 붙여넣기 해주시면 됩니다. <br>
(해당 링크에서 처음으로 나오는 코드입니다.) <br>

```
// vite.config.js
import vue from '@vitejs/plugin-vue'

export default {
  plugins: [vue()],
}
```

이제 비트 설치가 끝났습니다.

package.json에서 script 태그 안에서 dev라는 이름응로 vite를 추가해줍니다.

```
"dev": "vite",
```

이후 실행시 다음 명령어를 실행하면 됩니다.

```
npm run dev
```

### 컴포넌트를 사용하는 이유
- 컴포넌트를 사용하면 UI를 재사용 할 수 있습니다.
  - 프론트엔드 개발을 하다보면 JavaScript 뿐만 아니라 HTML, CSS를 반복적으로 사용할 때가 있습니다. <br> 이런경우 컴포넌트로 캡슐화 한 후 필요한 곳에서 사용할 수 있습니다.
- 컴포넌트를 사용하여 UI를 독립적으로 나눔으로써(레이아웃 등) 코드를 클린하게 할 수 있습니다.
  - 프론트엔드 개발을 하다보면 코드가 길어져 유지보수가 힘들 수 있습니다. <br> 이런경우 컴포넌트로 독립적으로 분리함으로써 코드를 클린하게 하여 유지보수를 보다 쉽게할 수 있습니다.


</details>

<details>
<summary>프로젝트 구성</summary>

#### Vue 설치방법

CLI를 사용하면 명령어 하나로 프로젝트를 scaffolding 할 수 있기 때문에 편리합니다.<br><br>

**scaffold**이란?
- 개발을 용이하게 시작할 수 있는 발판을 제공해주는 것을 의미합니다.

<br>
CLI로 시작하는 방법은 두 가지가 있습니다. <br>

#### Vue CLI
Vue CLI는 웹팩 기반 빌드도구입니다. <br>
하지만, Vue CLI는 현재 유지관리 모드에 있으므로, <br>
특정 웹팩 기능에 의존하지 않는 한 vite로 새로운 프로젝트를 시작하는 것을 공식문서에선 권장하고 있습니다.

#### Vite
Vite는 Vue SFC를 지원하고 매우 가볍고 빠른 빌드 도구입니다. <br>
Vue!의 저자이기도 한 Evan You가 만들었습니다. <br>

- Vite는 개발 서버를 구동할 때 매우 빠릅니다.
- 소스 코드의 변경이 일어났을 때 전체 모듈을 번들링 하는 것이 아니라, 변경된 모듈만 교체하기 때문에 개발을 더욱 더 빠르게 진행할 수 있습니다.

### vite로 프로젝트 구성하기

다음 명령어를 입력하여 vite로 프로젝트를 구성할 수 있습니다.

```
npm init vue
```

해당 명령어로 공식 Vue 프로젝트 스케폴딩 도구인 `create-vue`를 설치하고 실행합니다. <br>
프로젝트 이름을 설정한 후, 마지막 ESLint(코드 검사기)와 Prettier외엔 다 no를 선택해줍니다. <br>
그럼 프로젝트 이름으로 설정한, 디렉터리가 생깁니다. <br>
이 폴더가 프로젝트 디렉터리입니다. <br>

CLI를 통해 해당 디렉터리로 이동하여, 다음 명령어로 의존된 라이브러리를 설치합니다. <br>

```
npm install
```

설치 완료 후, 다음 명령어로 실행합니다.

```
npm run dev
```

터미널에서 나오는 경로를 통해 Vue로 진입할 수 있습니다.

</details>

<details>
<summary>ESLint, Prettier</summary>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/12a551fa-661b-4645-ab5e-1eb69b7dec66/image.png">
</div>

이 사진은 현재 프로젝트의 폴더 구조입니다. <br><br>

맨 마지막의 **vite.config.js**sms vite의 환경 설정파일입니다. <br>
vite 명령어를 사용할 때 해당 파일을 참고합니다. <br><br>

vite.config.js에서 alias 탭이 있는데, <br>
왼쪽 항목의 URL의 매개변수를 가리킨다는 의미입니다. <br><br>

```
'@': fileURLToPath(new URL('./src', import.meta.url))
```

이렇게 설정되어있는데, `@`이 `./src` 경로를 가리킨다는 의미입니다. <br><br>

현재 디렉터리가 src인데, src안에 component 안에 TheWelcome.vue 파일이 있습니다. <br><br>

만약 이 파일을 import 할 때 <br>

```
import TheWelcome from './components/TheWelcome.vue'
```

이렇게 쓸 수도 있지만, 다음처럼 사용할 수도 있습니다.

```
import TheWelcome from '@/components/TheWelcome.vue'
```

기본적인 내용은 생략합니다. <br>
~~(Vue 이전 강의에 다 나오거든요 ㅎㅎ)~~

**public** 디렉터리는 정적 리소스를 담고 있는 디렉터리입니다. <br>
src 하위의 **asset** 디렉터리는 웹팩이나 vite와 같은 빌드도구의 영향을 받는 이미지나 CSS 등 정적인 리소스를 담는 디렉터리입니다.

그리고 src하위의 **App.vue** 컴포넌트가 루트 컴포넌트입니다.<br>

---

### Vue 스타일 가이드

애플리케이션을 개발할 때 코드 컨벤션, 코드 스타일은 협업할 때 굉장히 중요합니다. <br>
예를 들어, 자바스크립트에서 홑따옴표로 감쌀지, 쌍따옴표로 감쌀지, 명령문 끝에 세미콜론을 넣을지 안 넣을지 등등 <br>
이러한 규칙을 **스타일**이라고 합니다. <br><br>

Vue의 스타일 가이드는 JavaScript나 HTML에 대한 제한을 최대한 피합니다. <br>

하지만 **뷰 스타일 가이드**에서 제안하고 싶은 점은 <br> 
뷰로 구현할 때 특정 스타일로 개발을 하게 되면 굉장히 유용하다는 점이 있는데, <br>
이러한 규칙을 4가지 범주로 나눠서 제안을 하고 있습니다 <br><br>

즉, 뷰로 개발할 때 어떤 점이 좋았다 혹은 어떤 점이 별로였는지 이러한 경험을 알려주는 가이드입니다.<br>

### 규칙 범주 

#### 필수
- 컴포넌트 이름에 합성어 사용
  - 예시로 todo라는 것보단, **todo-item**과 같이 합성어로 사용하는 게 좋다고 합니다.
- Prop 정의
  - 배열로 간단하게 정의하는 것보다 **객체로 상세하게 정의하는 것**이 좋고, **최소한의 타입은 정하는 것**을 가이드하고 있습니다.
  - `.eslintrc.cjs` 파일에서 module.exports 하위의 root 하위의 'eslint:recommended' 부분은 ESLint에서 다음과 같이 체크된 부분이 있습니다. <br> 
  이 부분은 "해당 항목은 자동으로 검사해라"라는 옵션이라고 보시면 됩니다.
  <div align="left">
    <img src="https://velog.velcdn.com/images/tjdtn4484/post/a1be217a-8de4-4266-b9ba-92bbe8d9e6a8/image.png">
  </div>
- `@vue/eslint-config-prettier` 옵션은 불필요한 규칙 혹은 ESLint 와 Prettier와의 충돌할 수 있는 규칙을 끄는 충돌방지용 옵션입니다.

### ESLint 속성추가

프로젝트 설정처럼 하다보면, '.eslintrc.cjs'이 있습니다. <br>
커스텀 컨벤션, 룰을 추가하려면 `rules` 속성을 추가해야합니다.

```
  "rules": {
    "no-console": "error", // 콘솔 사용시 Error가 발생합니다.
    "no-console": "warn", // 콘솔 사용시 경고표시가 발생합니다.
    "no-console": "off", // no-console 옵션 사용을 비활성화합니다.
    
  },
```

참고로 WebStrom을 사용 중인데, 추가해도 에러가 발생하지 않으면, Settings에서 **ESLint**를 검색하여 선택 후, <br>
**Disable ESLint**로 되어있는 것을 **Manual ESLint configuration**으로 변경하여 적용해주시면 됩니다. 

강의에서는 다음과 같이 설정합니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/0633b516-413a-47d8-947d-2ff02f6db184/image.png">
</div>

해당 파일들에 ESLint를 적용하고, 저장을 누를 때, 자동으로 ESLint가 적용되는데, 컨텐츠 제작자는 VScode를 통해서 설정합니다. <br>
하지만, 저는 JetBrain의 WebWtorm을 사용하므로, 위와 같이 적용하려면 다음과 같이 해주시면 됩니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/c7e9d8c8-4a98-4d9c-b594-4dfceda87e67/image.png">
</div>

settings-ESLint를 검색 후, 선택해주셔서 위와 같이 해주시면 됩니다. <br><br>

이후, main.js 혹은 App.vue에서 저장을 하면 깔끔하게 정리됩니다. <br><br>

그리고 전체 파일을 적용하려면, 터미널을 통해서 다음 명령어를 입력하면 됩니다.

```
npm run lint
```

그러면 전체적으로 lint 검사가 진행되는 것을 알 수 있습니다. <br><br>

그리고 ESLint를 적용한다면, Prettier를 비활성화 해줍니다. <br>


</details>

