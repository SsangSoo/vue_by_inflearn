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

### 규칙 예시
- 컴포넌트 이름에 합성어 사용
  - 예시로 todo라는 것보단, **todo-item**과 같이 합성어로 사용하는 게 좋다고 합니다.
- Prop 정의
  - 배열로 간단하게 정의하는 것보다 **객체로 상세하게 정의하는 것**이 좋고, 아니라면 최소한 **타입은 정하는 것**을 가이드하고 있습니다.
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

참고로 저는 WebStrom을 사용 중인데, 따로 설정을 해야하는 것 같습니다. <br>
혹여 위의 코드를 추가해도 에러가 발생하지 않으면, Settings에서 **ESLint**를 검색하여 선택 후, <br>
**Disable ESLint**로 되어있는 것을 **Manual ESLint configuration**으로 변경하여 적용해주시면 됩니다. 

강의에서는 다음과 같이 설정합니다. 

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/0633b516-413a-47d8-947d-2ff02f6db184/image.png">
</div>

다음은 ESLint를 적용 후, 파일마다 빨간 줄이 나오는데, 이걸 일일이 적용하기엔 귀찮습니다. <br>
따라서, 일괄적으로 저장하는 법을 보겠습니다. <br><br>

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

<details>
<summary>Options API VS Composition API</summary>

Vue2는 Options API를 사용했지만, Vue3가 나오면서 Composition API가 나왔고, <br>
Vue 진영에서도 Composition API를 이용하여 개발하기를 권장하고 있습니다.

#### Option API 스타일

```
    data() {
		return {
			counter: 0,
		};
	},
	methods: {
		increment() {
			this.counter++;
		},
	},
	mounted() {
		console.log('컴포넌트가 마운트 되었습니다');
	},
```

위와 같이 상태 데이터는 데이터 안에 선언하고,<br>
메서드는 메서드 안에 선언하고, <br>
컴포넌트가 마운트 되었을 때는 마운트 메서드를 선언해서 작성하는 방식입니다. <br>

#### Composition API 스타일

```
    setup() {
		const counter = ref(0);
		const increment = () => counter.value++;

		onMounted(() => {
			console.log('컴포넌트가 마운트 되었습니다');
		});

		return {
			counter,
			increment,
		};
	},
```

위의 코드와 같이 setup 함수 안에 그룹핑 해놓은 스타일이 컴포지션 API 입니다. <br><br>

Vue 공식문서를 통해서 API의 함수들을 더욱 자세히 확인할 수 있습니다. <br>

### 컴포지션 API가 나온 배경

Optinos API 같은 경우, 데이터, 메서드 등의 코드를 보면 **동일한 논리적 관심사를 처리하는 코드가 분산**이 되어있습니다.<br> <br>

만약 코드가 길어지면, 복잡해져서 스크롤을 한창 아래로 내려야합니다. <br><br>

하지만, 컴포지션 API를 사용하게되면, **동일한 논리적 관심사를 그룹핑**할 수 있습니다.<br>
코드를 그룹핑함으로써 분석하기 쉽고, 유지보수가 용이해집니다. <br><br>

만약 코드를 다른 곳에서 사용한다면, <br>
관심사가 동일한 코드를 가지고 유틸 파일로 만들 수 있습니다. <br><br>

하지만 Options API는 코드조각을 일일이 찾아야 됩니다. <br>
번거롭게요... <br><br>

그리고 Composition API를 사용하면, 동일한 관심사 코드를 그룹핑하고, 추출하여 쉽게 재활용 가능합니다. <br>
이 때 **관심사를 추출하여 재사용 가능한 코드**를 컴포지션 API에서는 **컴포저블**이라고 부릅니다. <br><br>

컴포저블은 OptionsAPI에서 사용했던 믹스인의 모든 단점을 해결해줍니다. <br>
또한, <br>
Vue3의 재사용이 가능한 함수를 활용하면, 믹스인을 사용할 필요도 없습니다.<br><br>

**정리하자면**,<br>
- 컴포지션 API는 코드 조각을 그룹핑함으로써 분석을 용이하게 합니다.
- 컴포저블 함수를 사용해서 애플리케이션 전체에서 코드를 매우 쉽게 재사용할 수 있게 해줍니다.


### OptionsAPI, CompositionAPI의 관계

- CompositionAPI는 OptionsAPI의 대부분의 기능을 대체합니다. 
  - 하지만, 경우에 따라 필요한 경우 OptionsAPI를 사용해야 할 수도 있습니다.

- OptionsAPI, CompositionAPI를 같이 사용할 수도 있습니다.
  - 기존 OptionsAPI로 개발을 했지만, Composition API의 기능이 필요한 경우에만 사용하는 것이 좋습니다.
  - 새로운 프로젝트를 진행할 떄는 CompositionAPI를 기반으로 개발하는 것이 좋습니다.

비교하기 좋은 사이트는 다음과 같습니다. <br>
[뷰 3 공식문서](https://vuejs.org/)입니다.

해당 사이트에서 Docs의 Guide를 선택합니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/b116b526-dd97-4299-be02-dc3c38a985b5/image.png">
</div>


그리고, 왼쪽 상단의 **Options** 혹은 **Composition** 토글을 통해서 두 API 방식을 비교할 수 있습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/7f42a891-b794-46b3-866e-7ee4f26ee209/image.png">
</div>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/aa26cf22-d7ff-4c14-be26-f3386c7d80e7/image.png">
</div>


</details>

<details>
<summary>Composition API</summary>

컴포지션 API는 성격에 따라 **반응형 API**, **라이프 사이클 Hook**, **종속성 주입** 으로 구분됩니다.<br><br>


### 반응형 API
- 말 그대로 반응하는 데이터와 관련된 API 세트라고 보시면 됩니다. <br><br>

#### 반응형이란?

다음과 같이 App.vue 코드를 작성합니다.<br><br>


```
<template>
	<div>
		<h2>반응형 메시지</h2>
		<p>{{ reactiveMessage }}</p>
		<h2>일반 메시지</h2>
		<p>{{ normalMessage }}</p>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const reactiveMessage = ref('Hello Reactive Message');
		const normalMessage = 'Hello Nomal Message';

		return {
			reactiveMessage,
			normalMessage,
		};
	},
};
</script>

<style lang="scss" scoped></style>

```

그럼 다음과 같이 나올 것입니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/a497ab54-2a2f-4a59-b737-6e48fb9765c9/image.png">
</div>

그리고 버튼을 누르면, `!`를 추가하는 코드를 작성해보겠습니다.<br><br>

```
		<h2>반응형 메시지</h2>
		<p>{{ reactiveMessage }}</p>
		<button v-on:click="addReactiveMessage">Add Message</button>
		<h2>일반 메시지</h2>

		...
		
		const reactiveMessage = ref('Hello Reactive Message');
		const addReactiveMessage = () => {
			reactiveMessage.value = reactiveMessage.value + '!';
		};
		const normalMessage = 'Hello Nomal Message';

		return {
			reactiveMessage,
			normalMessage,
			addReactiveMessage,
		};
...

<style lang="scss" scoped></style>
```

그리고 메세지를 클릭해보면, <br><br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/0cb12eba-3746-4d52-86d4-c4e225e63ab1/image.png">
</div>

위 그림처럼 느낌표가 붙습니다.(3번을 눌렀기 때문입니다.) <br><br>

선언했던 `reactiveMessage`이 반응형 메세지였는데, <br>
이 **반응형 메세지의 상태가 변경됨**에 따라, **UI도 함께 변경**되는 것을 확인할 수 있습니다. <br><br>

그 이유는 ref API를 사용했기 때문입니다.<br><br>

반면에, 일반메세지는 어떻게 될까요? <br><br>

다음과 같이 코드를 작성합니다.<br><br>

```
  ...
        <h2>일반 메시지</h2>
		<p>{{ normalMessage }}</p>
		<button v-on:click="addNomalMessage">Add Message</button>
  
  ...
        const normalMessage = 'Hello Nomal Message';
        const addNomalMessage = () => {
            addNomalMessage.value = addNomalMessage.value + '!';
        };

		return {
			...
			addReactiveMessage,
			addNomalMessage,
  ...
```

그러면 다음과 같이 나오는데, <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/d86ca3c5-35f5-472a-824f-db10e5e4f31c/image.png">
</div>

위 그림은 버튼을 몇 번 클릭한 모습입니다.<br><br>

이 말인 즉슨, 반응형 메시지가 아니라면,  <br>
음... 네... <br>


<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/edffdb4b-5995-4394-9e73-ae9420234bbd/image.png">
</div>

그렇습니다..

이처럼 반응형 API는 반응형 데이터를 선언하거나, 혹은 <br>
그와 관련된 일을 하는 API입니다.<br><br>


```
isRef() // 반응형인지 확인하는 문법
```

콘솔을 통해서 반응형인지 아닌지를 보도록 하겠습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/9da7c4ca-0fb7-4100-bb40-93f4d444ee85/image.png">
</div>

결과는 위 그림과 같습니다.
따라서 반응형 API란 **반응형과 관련된 일을 하는 API다**라고 보시면 됩니다.


### 라이프 사이클 Hook

Vue 인스턴스나 컴포넌트가 생성될 때, 미리 사전에 정의된 몇 단계의 과정을 거치게 되는데 이를 **라이프 사이클(Lifecycle)**이라고 합니다. <br>
라이프사이클 단계에서 실행되는 함수를 **라이프 사이클 훅**이라고 합니다.<br><br>

예를 들어 어떠한 코드를 컴포넌트가 DOM에 마운트 되기 전에 넣고 싶거나, 혹은 마운트된 후에 넣고 싶을 때, <br>
onBeforeMount, onMounted와 같은 API를 사용할 수 있습니다.


### 종속성 주입

해당 내용은 추후에 다룹니다.

</details>

<details>
<summary>Setup 함수</summary>

Setup() 함수(hook)은 Composition API 사용을 위한 진입점 역할을 합니다. <br>

Setup 함수는 라이프 사이클 다이어그램을 보면, 컴포넌트 인스턴스가 생성되기 전에 실행되는 Hook이라고 볼 수도 있습니다. <br>
<br>
Setup 함수 안에 반응형 상태, 메서드를 선언하고, 객체로 반환하게 되면 템플릿에 노출할 수 있습니다.<br>

```
<template>
	<div>
		<p>
			{{ counter }} // return문 안에 있음. 사용 가능
		</p>
		<p>
			{{ message }} // return문 안에 없음. 사용 불가
		</p>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const counter = ref(0);
		const message = ref('Hello Vue3');
		return {
			counter,
		};
	},
};
</script>
```

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/e350b359-e098-49fc-ba98-06473255c78e/image.png">
</div>

이처럼 return 문 안에 있냐 없냐에 따라 템플릿 내에서 사용할 수도 있고, 사용하지 못할 수도 있습니다.<br>
이는 변수 뿐만 아니라, 메서드도 마찬가지입니다. <br><br>

템플릿 뿐만 아니라, 컴포넌트 인스턴스에서도 사용할 수 있습니다.<br>

```
<script>
import { ref } from 'vue';

export default {
	setup() {
		const counter = ref(0);
		const message = ref('Hello Vue3');
		return {
			counter,
		};
		
		mounted() {
		  console.log(this.counter) // 0
		}
	},
};
</script>
```

위와 같이 mounted 안에서 this 키워드를 이용하여 접근할 수 있습니다. <br>
(참고로 이 부분은 OptionsAPI입니다.) <br><br>


- props
그리고 Setup 함수의 첫 번째 매개변수는 props입니다. <br>
**props**는 추후에 다룹니다.^^<br>
Setup 함수의 첫 번째 매개변수로 props가 넘어온다는 정도로 알고 가면 됩니다. <br>

- Setup Context
두 번째 매개변수로는 Setup Context 객체입니다.<br>
컨텍스트 객체는 Setup 함수 내에서 유용하게 사용할 수 있는 속성을 갖고 있습니다. <br><br>

속성은 다음과 같이 있습니다. 
- context.attrs
- context.slots
- context.emit
- context.expose
  
<br> 이러한 기능들도 추후에 배웁니다 ^^

</details>


<details>
<summary>템플릿 문법</summary>

### 텍스트 보간법
텍스트 보간법은 데이터 바인딩의 가장 기본형태로 `{{ data }}` 처럼 이중 중괄호(콧수염 괄호라고도 불립니다.)를 사용하는 것입니다. <br><br>
이중중괄호({{}})를 활용하여, 데이터에 바인딩할 수 있습니다. <br><br>

그러면 script 태그 안의 값이 변경됨에 따라, 템플릿에서 보여지는 값도 변경됩니다. <br><br>

만약에 한 번만 렌더링을 하고 데이터가 변경되지 않도록 하려면, **v-once**라는 디렉티브를 사용하면됩니다. <br><br>

잠깐! 여기서 **디렉티브**란? <br>
`v-`와 같은 prefix가 붙는 특수한 속성입니다. <br>
디렉티브는 엘리먼트 혹은 컴포넌트에게 행동을 지시하는 것을 말합니다.<br><br>

`v-once`는 **일회성으로만 보관하고, 갱신해도 변경하지 말라**는 기능이 있는 디렉티브입니다.<br><br>

```
<template>
  <h2>보간법</h2>
		<p>{{ message }}</p>
		<p v-once>{{ message }}</p>
		<button v-on:click="message = message + '!'">Click!</button>
</template>
<script>
import { ref } from 'vue';

export default {
	setup() {
		const message = ref('안녕하세요!');
		return {
			message,
		};
	},
};
</script>
```

위와 같이 있을 때, <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/5e80105b-fb0e-4359-ab5d-5646a00533b7/image.png">
</div>

`v-once`가 적용된 곳은 처음과 같지만, 그냥 바인딩된 곳에는 느낌표가 많이 붙은 것을 확인할 수 있습니다. <br>

### 이중중괄호({{}})
이중중괄호는 데이터를 HTML이 아닌, 일반 텍스트로 해석합니다. <br>
실제 html을 출력하려면, `v-html` 디렉티브를 사용해야합니다. <br><br>

```
  ...

  <h2>v-html</h2>
  <p>{{ rawHtml }}</p>
  <p v-html="rawHtml"></p>

  ... 

Setup() {
  const rawHtml = ref('<strong>안녕하세요</strong>');
  
  ... 
  
  return {
    rawHtml,
  }
}

```

위와 같이 있을 때, 다음과 같이 나타납니다. <br> 

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/bfdaaadb-6910-4bb9-b99d-d32600a3e776/image.png">
</div>

<br><br>

### v-html
`v-html` 디렉티브를 사용하면, 태그 내에 아무것도 선언하지 않고, 디렉티브의 값으로만 주면 해당 태그가 템플릿에 적용됩니다. <br><br>

```
<p v-html="rawHtml"></p>
```

#### v-html 주의점
`v-html`을 실무에서 사용하게 되면, HTML을 동적으로 웹사이트에서 렌더링하게 되는데 **XSS 취약점(크로스 사이트 스크립팅)**에 위험해집니다. <br>
<br>
**XSS 취약점(크로스 사이트 스크립팅)**은 웹사이트에서 악성 스크립트를 삽입할 수 있는 취약점입니다.<br>
따라서, 관리자가 입력하는 컨텐츠거나, 혹은 신뢰할 수 있는 컨텐츠에서만 사용을 하고, <br>
사용자가 제공하는 컨텐츠에서는 사용하지 않는 것을 권장합니다.<br><br> 

### 속성 바인딩(v-bind)
속성을 바인딩할 때는 `v-bind` 디렉티브를 사용할 수 있습니다.<br>

```
<div v-bind:title="dynamicTitle">
	마우스를 올려보세요. 마우스가 올라가면 보여요!
</div>

 ...
 
 const dynamicTitle = ref('안녕하세요!!!!');
 
 ...
 
 return {
			dynamicTitle,
  }
```

그리고 마우스를 올려보면 다음과 같이 나옵니다. <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/3740a83c-5d58-4e3e-84d9-547c5ceb410b/image.png">
</div>

<br>

```
  ...
  
  <input type="text" value="홍길동" v-bind:disabled="isInputDisabled" />
  
  ...

  const isInputDisabled = ref(false);
  const isInputDisabled = ref(true);
  
  ...
```

위와 같이 작성하게되면, isInputDisabled의 값이 true이냐 false이냐에 따라, <br>
input 값이 수정될 수도 있고, 안 될 수도 있습니다. <br><br>


<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/d648f7ac-54e4-4ba5-9e1e-b9f37f9b519b/image.png">
</div>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/54657829-aa9d-446e-85fd-a87b3e38d12e/image.png">
</div>

그리고 `v-bind`는 단축 속성을 지원합니다! <br><br>

`v-bind:` 이렇게 사용해도 되고, <br>
`:` 이와 같이 콜론(:)만 사용해도 됩니다! <br><br>

앞으로의 수업은 단축 속성을 사용한다고 합니다.^^ <br><br>

그리고 `v-bind`는 여러 개의 속성을 한 번에 바인딩할 수 있습니다. <br>
다중 속성을 객체로 한 번에 바인딩할 수 있습니다. <br>

```

...
  <input v-bind="attr" />
...

  const attr = ref({
			type: 'password',
			value: '12345678',
			disable: false,
		});
		
...
 
  return {
			attr,

```

위와 같이 한 번에 정의하여 사용할 수 있습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/bcd7d52c-3e0b-4511-86ab-85268e19d9a3/image.png">
</div>

현재 비밀번호가 잘 들어간 것을 확인할 수 있습니다.
<br>

```
type: 'text',
```

타입을 text로 바꾸면 다음과 같이 됩니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/00f5643d-86b8-4a2a-9ec3-cc9fcb829661/image.png">
</div>

이렇게 다중 속성을 바인딩할 수 있습니다.

### 이중괄호 안의 자바스크립트 표현식
이중괄호문에서는 데이터 뿐만 아니라, 자바스크립트 표현식도 가능합니다. <br>

```
		<h2>JavaScript</h2>
		{{ message.split('').reverse().join('') }} <br />
		{{ isInputDisabled ? '예' : '아니오' }}
```

아래는 결과입니다. <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/1cc770bc-bd02-4fa8-b26f-5f03a98ffde3/image.png">
</div>

이처럼 JavaScript 표현식도 가능합니다.

</details>

<details>
<summary>반응형 기초(Reactivity)</summary>

자바스크립트 객체에서 반응형 상태를 생성하기 위해서 `reactive()` 함수를 사용할 수 있습니다. <br>
리액티브 함수에 객체를 넣음으로 반응형 상태를 선언할 수 있습니다. <br>
이 때 반환되는 데이터를 반응형 객체라고 하고, 반응형 객체가 변경되면 바인딩된 화면도 자동으로 업데이트 됩니다. <br><br>

```
<template>
	<div>
		<button v-on:click="increment()">Click {{ state.count }}</button>
	</div>
</template>

<script>
import { reactive } from 'vue';

export default {
	setup() {
		const state = reactive({
			count: 0,

		});
		const increment = () => {
			state.count++;
		};
		return {
			state,
			increment,
		};
	},
};
</script>
```

반응형은 Depth가 깊어도 제대로 동작을 합니다.<br>

```

    ...
    
    <button v-on:click="increment()">Click {{ state.count }}</button>
    <button v-on:click="increment()">Deep Click {{ state.deep.count }}</button>

    ...

    export default {
        setup() {
            const state = reactive({
                count: 0,
                deep: {
                    count: 0,
                },
            });
            const increment = () => {
                state.count++;
                state.deep.count++;
            };
            return {
                state,
                increment,
            };
        },
};
	...
```

아래는 해당 코드의 결과입니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/d8c3b64a-82a8-48e2-b67c-6198fd6678d3/image.png">
</div>

이처럼 얕은 Depth부터 깊은 Depth까지 반응형으로 동작하는 것을 확인할 수 있습니다. <br><br>

OptionsAPI에서는 data라는 옵션의 객체를 return해서 선언하는데, 내부적으로 반환된 객체는 reactive로 감싸진다는 것을 참고하시면 될 거 같습니다.<br><br>

**reactive**함수는 객체나 배열과 같은 **레퍼런스 타입을 반응형 객체로 만들 수 있습니다.** <br><br>

그럼 string, number, boolean과 같은 기본형을 반응형 데이터로 만드려면 어떻게 해야할까요? <br>
이에 대해 알아보겠습니다. <br>

```
<template>
	<div>
		<p>{{ message }}</p>
		<button v-on:click="addMessage">add click</button>
	</div>
</template>

<script>
import { reactive } from 'vue';

export default {
	setup() {
		let message = reactive('Hello Vue!');
		const addMessage = () => {
			message = message + '!';
		};
		return {
			message,
			addMessage,
		};
	},
};
</script>
```

해당 코드의 결과는 다음과 같습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/d773696b-af43-4337-be5f-8964044c7111/image.png">
</div>

그런데, 반응형으로 동작하지 않는다는 것을 확인할 수 있습니다. <br>
그 이유는 **reactive함수**는  객체나 배열과 같이 레퍼런스 타입의 반응형 상태, 반응형 객체를 선언하는 함수이기 때문입니다. <br>

```
console.log('message :', message);
console.log('message typeof :', typeof message);
```

해당 코드를 넣고, 확인을 해보면, 

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/681c8032-2c5d-42ab-8a2b-e2bd6d11d679/image.png">
</div>

string 타입임을 확인할 수 있습니다. <br><br>

return하는 message 값과 템플릿에서 사용되는 message 값이 메모리 주소를 가지고 서로 공유를 해야하는데, <br>
기본형 특성상 값 자체가 바뀜으로써 메모리를 통해서 공유되지 않습니다. <br>
그렇기 때문에, 당연히 반응형으로 동작하지 않습니다. <br><br>

만약에 기본형을 반응형으로 다루려면, 이미 약속된 속성을 선언하고, 내부에 선언해야합니다. <br>

```
setup() {
  let message = reactive({
    value: 'Hello Vue!',
  });
  const addMessage = () => {
    message.value = message.value + '!';
  };
}
```

위의 코드처럼 작성하면 됩니다. <br>
그러나 이는 결국 Primitive 타입 즉, 기본형이 아니라 객체를 선언한 것입니다. <br><br>

따라서 반응형 API에서는 기본형을 선언할 수 있는 ref함수를 제공합니다. <br>

### ref
`reactive()` 함수는 객체타입에만 동작합니다.<br>
반면에, `ref()` 함수는 기본타입을 반응형으로 만들 수 있는 반응형 API입니다. <br><br>

ref 함수를 사용하려면, <br>
다음과 같이 ref 내부에 Primitive 타입을 넘기면 됩니다. <br><br>

```
const count = ref(0);
```

그러면, 반응형 데이터를 반환하게 됩니다. <br>
이 ref로 반환된 반응형 데이터는 **변이 가능한 (mutable) 객체**를 반환합니다.<br>
이 객체 안에는 `value`라는 하나의 속성만 포함하는데, <br>
value라는 속성은 매개변수로 던졌던 Primitive 타입을 가지고 있습니다.<br>
(위의 코드로 보면 0입니다.) <br><br>

이 반응형 객체는 value값에 참조역할을 하는 것입니다. <br>

결론적으로 ref함수로 기본형타입을 선언하게 되면, 내부적으로 value라는 값을 가지게 되고, <br>
`.value`를 선언하지 않더라도 ref함수로 선언된 값은 내부의 `.value`값을 호출한다고 보면 될 거 같습니다.

```
<template>
	<div>
		<p>{{ message }}</p>
		<button v-on:click="addMessage">add click</button>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		let message = ref('Hello Vue!');
		const addMessage = () => {
			message.value = message.value + '!';
		};
		console.log('message :', message.value);
		console.log('message typeof :', typeof message.value);
		return {
			message,
			addMessage,
		};
	},
};
</script>
```

위의 코드에서 message를 ref함수로 선언했지만, <br>
템플릿에서는 `message.value`가 아닌 `message`를 이중괄호문으로 호출했습니다.  <br><br>

그리고 잘 반응합니다. <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/c2c30a16-61a5-4d5c-80d1-25396c604ebf/image.png">
</div>


그리고, 콘솔로 확인하면, message 내부의 value값이 래핑된 것을 확인할 수 있습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/ba2b0556-eec7-4106-80b9-280ec15e2ac7/image.png">
</div>

<br>

그리고 크롬에서 Vue devtools를 보면 다음과 같이 ref 함수로 선언한 것은 Ref의 표시가 나오고, 편집이 가능하도록 연필 모양이 나옵니다.<br>
<br>
<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/649b0024-7e9e-4d0e-8a0a-f32d16b57b03/image.png">
</div>

#### ref함수를 reactive의 객체를 정의할 때 속성으로 넣게되면?

```
const count = ref(0);
const state = reactive({
  count
 })
```

이처럼 ref함수를 reactive의 객체를 정의할 때 속성으로 넣게되면 어떻게 될까요? <br><br>

이에 대해 알아보도록 하겠습니다.<br>

```
const count = ref(0);
const state = reactive({
    count,
});
console.log(count.value);
// console.log('state.count : ', state.count.value); // undefined
console.log('state.count : ', state.count);   // 0
```

ref로 선언한 데이터를 반응형 객체의 속성으로 주입하게 되면,  <br>
자동으로 해당 데이터의 value는 언래핑되어 사라집니다. <br>
그래서 일반 속성을 사용하는 것처럼 사용할 수 있습니다. <br>
그리고 반응형은 여전히 연결되어 있습니다.

```
const count = ref(0);
const state = reactive({
    count,
});
count.value++;
count.value++;
console.log(count.value); // 2
console.log('state.count : ', state.count); // 2
```

이와 같이 count.value의 값이 증가함에 따라, <br>
state.count도 증가한 것을 확인할 수 있습니다. <br><br>

배열에선 조금 다릅니다.

```
// ref -> Array
const message = ref('Hello');
const arr = reactive([message]);
console.log('arr[0]: ', arr[0]);
console.log('arr[0].value: ', arr[0].value);
```

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/80bcc2cd-5b3d-4254-9e82-cc80231d1e5d/image.png">
</div>

배열을 통해서 접근하려면, `.value`를 통해서 접근해야합니다.<br>
반응형 상태를 객체로 넣으면 `.value`를 붙이지 않아도 되지만, <br>
반응형 상태를 배열로 넣으면 배열에 접근하기 위해서 `.value`를 붙이면 됩니다. <br><br>

### 반응형 상태 구조 분해하기(Destructuring)

객체의 몇몇 속성을 사용하고 싶을 때, ES에서 구조 분해 할당을 사용하면 되는데,<br>
반응형 객체에서 구조분해 할당을 하게 되면 해당 속성들은 반응형을 잃게 됩니다. <br><br>

```
<template>
	<div>
		<p>author: {{ author }}</p>
		<p>title: {{ title }}</p>
	</div>
</template>

<script>
import { reactive } from 'vue';

export default {
	setup() {
		const book = reactive({
			author: 'Vue Team',
			year: '2020',
			title: 'Vue 3 Guide',
			description: '당신은 이 책을 지금 바로 읽습니다 ;)',
			price: '무료',
		});

		const { author, title } = book;
		console.log(typeof author);
		return { author, title, book };
	},
};
</script>
```

위와 같은 코드가 있을 때, <br>
크롬 브라우저의 확장 프로그램인 Vue devtools를 확인해보면, <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/75b357c2-5b78-47a0-8b4c-baf6497ff8d6/image.png">
</div>

이처럼 book은 reactive로 선언했기 때문에, 반응형이 살아있습니다. <br>
하지만, 구조분해할당으로 선언된 author, title은 변경할 수 없고, 콘솔을 통해 확인해보면, 그냥 string타입임을 확인할 수 있습니다. <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/4c5a3f49-c556-4152-8ad8-6b575aabdcee/image.png">
</div>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/b0362de8-3714-4b62-8154-391593bd1626/image.png">
</div>

그럼 반응성을 잃지 않으면서 구조분해할당을 할 수는 없을까... <br>
그 방법은 **toRef(), toRrefs() API**를 사용하면 됩니다.  <br>

```
const { author, title } = book        // 밑에처럼 변경
const { author, title } = toRefs(book);
```

toRefs(book)으로 값을 변경하면, 반응형 데이터가 됩니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/dada99fd-9068-4a54-ac78-8fb5227285ff/image.png">
</div>

이처럼 Ref가 붙은 것을 확인할 수 있고, <br>
값을 변경할 수 있겠죠..? <br><br>

toRefs()를 사용하게 되면 book에 있는 속성과 구조분해해서 재할당한 반응형 상태는 동기화가 됩니다.<br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/926817c9-ad06-463a-83f4-24b47ace5386/image.png">
</div>

저는 위의 author 데이터를 바꿨지만, book 내부의 author의 값도 바뀌었습니다. <br>
<br>
만약 구조분해할당이 아니라, 객체에서 하나만 가져오고 싶다면, `toRef()`를 사용하면 됩니다.<br>

```
const author = toRef(book, 'author');
```

이처럼 속성하나만 선언하고, toRef의 첫 번째 매개변수에는 객체, 두 번째 매개변수에는 객체의 내부 값을 가지고 선언하면 됩니다. <br>

따라서 구조분해할당으로 가져온 데이터가 반응형을 잃지않도록 하려면, toRef, toRefs를 사용하면 됩니다. <br><br>

### readonly

readonly를 이용하면 반응형 객체의 변경을 방지할 수 있습니다. <br>

```
const original = reactive({ count: 0 });

const copy = readonly(original);

original.count++;

copy.count++;
```

위와 같이 readonly를 통해서 original의 값을 복사하여 copy로 선언하면,<br>
original.count 즉 원본 값은 변경할 수 있지만, <br> 
복사본인 copy.count는 변경할 수 없습니다. <br><br>

예를 들어, 컴포넌트 A와 B가 있을 때, <br>
A의 컴포넌트에서 사용한 반응형 상태가 B 컴포넌트에서도 필요합니다. <br>
A 컴포넌트에서 B 컴포넌트에 반응형 데이터를 주입해줄 수 있는데, <br>
B 컴포넌트에서 데이터를 변경하면, 원본이 있는 A 컴포넌트도 동기화되어 변경됩니다.<br>
이러한 경우 readonly를 이용해서 변경불가능한 객체를 만들어서 B 컴포넌트로 주입하면 됩니다. <br><br>

```
<script>
import { reactive, readonly } from 'vue';

export default {
	setup() {
		const original = reactive({
			count: 0,
		});
		original.count++;
		console.log(original.count);

		return {};
	},
};
</script>
```

콘솔에서 1이 출력됨을 확인할 수 있습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/520a795d-d15d-42d2-a415-9f8c5018f43a/image.png">
</div>

readonly를 사용하여 콘솔을 출력하면 다음과 같습니다.

```
const original = reactive({
    count: 0,
});
const copy = readonly(original);
original.count++;
console.log('original.count : ', original.count);
console.log('copy.count : ', copy.count);
```

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/520a795d-d15d-42d2-a415-9f8c5018f43a/image.png">
</div>

만약 copy.count를 변경하려 하면, 해당 값은 readonly 이기 때문에, 변경할 수 없다는, 것을 확인할 수 있습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/87d06188-1626-4bda-8845-ff987a1b72db/image.png">
</div>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/c9ae67b5-8d5f-4a8e-b0ab-36451d30cba3/image.png">
</div>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/484de383-b8a7-4747-af4c-df457928ff67/image.png">
</div>


#### Reactivity Transform : 실험적인 단계

위에서 본 것처럼 refs와 함께 `.value`를 사용하는 것은 JavaScript의 언어 제약으로 인한 단점입니다. <br>
기본형 타입을 참조형 타입으로 다루기 때문입니다. <br>
뷰3에서는 compile-time transforms를 사용하여 적절한 위치에 `.value`를 자동으로 추가해서 불편함을 개선하려고 하고 있습니다.

`$`를 활용하는데, 

```
let const = $ref(0);

function increment() {
  count++;
}
```

이처럼 `$`를 이용해서 기본형을 ref 안에 선언했지만, <br>
increment의 내부에 `count.value`가 아닌, `count`만 선언한 것을 확인할 수 있습니다. <br><br>

실험적인 단계이므로, 바로 사용할 수 없겠지만, 참고하면 될 거 같습니다!! <br>

</details>

<details>
<summary>Computed</summary>

템플릿 문법( {{ }} )은 간단히 사용하면 매우 편리합니다. <br>
하지만, 템플릿 내 표현식 코드가 길어질 경우 가독성이 떨어지고 유지보수가 어려울 수 있습니다. <br><br>

이럴 때 사용하는 반응형 API가 **computed입니다**. <br>
computed를 사용하면 computed 안에 콜백 함수를 정의함으로써, return 되는 값을 속성으로 읽기 전용 속성으로 사용할 수 있습니다.<br><br>

```
<template>
	<div>
		<h2>{{ teacher.name }}</h2>
		<h3>강의가 있습니까?</h3>
		<p>{{ teacher.lecture > 0 ? '있음' : '없음' }}</p>
	</div>
</template>

<script>
import { reactive } from 'vue';

export default {
	setup() {
		const teacher = reactive({
			name: '짐코딩',
			lecture: ['HTML/CSS', 'JavaScript', 'Vue3'],
		});
		return {
			teacher,
		};
	},
};
</script>
```

위의 코드 중 `{{ teacher.lecture > 0 ? '있음' : '없음' }}` << 이 부분이 길어지고, 이러한 코드를 여러 번 사용한다면, 비효율적입니다. <br>
이 때 사용하는 것이 computed 함수입니다. <br>

```
<template>
  <p>{{ hasLecture }}</p>
</template>

<script>
const hasLecture = computed(() => (teacher.lecture > 0 ? '있음' : '없음'));
</script>
```

이렇게 computed를 사용하면 조금더 템플릿 문법이 간결해질 수 있습니다. <br>
그런데, 아래와 같이 똑같은 기능을 하는 메서드를 다음과 같이 선언하면 어떻게 될까요? <br>

```
<p>{{ existLecture() }}</p>

const existLecture = () => (teacher.lecture > 0 ? '있음' : '없음');
```

결과적으로는 같은 기능을 수행하므로, 결과가 같습니다. <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/946e9adb-e993-46b1-afd6-ff1c03fd057e/image.png">
</div>

똑같지만, 성능면에서는 computed를 사용하는 것이 더욱 좋습니다.<br>
왜냐하면, computed는 계산된 값이 캐싱되기 때문입니다. <br><br>

```
<template>
    <p>{{ hasLecture }}</p>
    <p>{{ hasLecture }}</p>
    <p>{{ existLecture() }}</p>
    <p>{{ existLecture() }}</p>
</template>
<script>
    const hasLecture = computed(() => {
        console.log('computed'); // 출력
        return teacher.lecture > 0 ? '있음' : '없음';
    });
    const existLecture = () => {
        console.log('method');    // 출력
        return teacher.lecture > 0 ? '있음' : '없음';
    };
</script>
```

위와 같이 선언되어있을 때, <br>
콘솔창을 확인해보면, 

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/a7877ab0-1e5b-494c-9b1c-0bf9d2959654/image.png">
</div>

이렇게 그냥 함수는 두번을 출력하지만, computed 를 사용한 곳은 한 번만 출력한 것을 확인할 수 있습니다. <br>
참고로 UI 결과는 다음과 같습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/fc81af43-21d6-4f63-b965-6cd905d5cfee/image.png">
</div>

그리고, 캐시가 다시 계산되는 시점은 <br>
**반응형 데이터가 변경되는 시점**입니다. <br><br>

그리고 Vue devtools에서 '더 보기'에서 `Highlight updates`를 켜주면, 

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/f0f8b955-8589-41b7-a868-faa35bb9dc42/image.png">
</div>

아래와 같이 highlight가 생기는 것을 확인할 수 있습니다.<br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/8659dcd8-70e9-4f25-952d-aa9ead91281a/image.png">
</div>

그러면 rendering 될 때마다, highlight 안의 값들을 다시 불러오는데, <br>
아래와 같이 버튼을 누르면, 데이터가 갱신됩니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/73ec17fa-d39a-482a-ad2a-2b5bcb0a8e32/image.png">
</div>

그런데 아래를 보시면, computed는 한번만 출력되고, 함수만 출력되는 것을 확인할 수 있습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/4e8cf655-28b3-4ccc-bb0b-7511f97ce564/image.png">
</div>

그 이유는 아까 말한 것처럼, computed는 캐싱을 사용하기 때문입니다. <br><br>

그리고 computed는 기본적으로 getter전용입니다.<br>
계산된 속성에 새 값을 할당하려고 하면 런타임 경고가 표시됩니다! <br>
computed에서 새 값을 할당할 필요가 있을 경우에은 getter와 setter함수를 사용해서 쓰기가 가능한 속성을 만들 수 있습니다. <br><br>


```
<template>
		<h2>이름</h2>
		<p>{{ fullName }}</p>
</template>

<script>
	const firstName = ref('홍');
    const lastName = ref('길동');

    const fullName = computed(() => firstName.value + ' ' + lastName.value);
</script>

```

이처럼 '홍 길동'이 출력되는 것을 확인할 수 있습니다. <br>

```
<script>
		const firstName = ref('홍');
		const lastName = ref('길동');

		const fullName = computed({
			get() {
				return firstName.value + ' ' + lastName.value;
			},
			set(value) {
				[firstName.value, lastName.value] = value.split(' ');
			},
		});
		console.log('Consol출력 :', fullName.value);
		fullName.value = '짐 코딩';
</script>
```

위와 같이 하게 되면, 
computed 안에서 `get()`은 getter역할을, `set()`은 setter의 역할을 합니다.

```
fullName.value = '짐 코딩';
```

이 부분에서 setter를 불러오게 되고, <br>
해당 값을 띄어쓰기로 split을 하여 firstName과 lastName에 할당합니다. <br>
<br>
그럼 결과적으로 짐 코딩이 출력되는 것을 확인할 수 있습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/7382ea68-80df-498b-9080-f6b965dbc622/image.png">
</div>

</details>

<details>
<summary>Class와 Style 바인딩</summary>
### DOM 요소의 클래스와 스타일 속성에 바인딩하는 방법

클래스를 동적으로 바인딩하려면, `v-bind`와 같은 디렉티블 사용해야했었는데요. <br>
`v-bind`를 통해 클래스와 인라인 스타일을 조작할 수 있습니다.<br><br> 

#### 클래스에 바인딩하는 방법
`v-bind`는 단축속성을 이용해서 <br>
`v-bind:class` 를 `:class`로 사용할 수 있었습니다. <br><br>

`v-bind:class`디렉티브는 일반 class속성과 공존할 수 있습니다. <br>
(다른 속성은 공존할 수 없지만, class는 특수하게 공존할 수 있습니다.) <br>

```
<template>
  <div :class="{ active: true }">텍스트입니다.</div>
</template>
```

이렇게하면 `active`가 **클래스에 바인딩**된 것을 확인할 수 있습니다. <br>
(참고로 객체로 바인딩할 수 있습니다.)

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/76cfac8c-be0b-40e7-99ed-3efa504556cf/image.png">
</div>

```
<template>
	<div>
		<div :class="{ active: isActive }">텍스트입니다.</div>
		<button v-on:click="toggle">toggle</button>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const isActive = ref(true);
		const toggle = () => {
			isActive.value = !isActive.value;
		};

		return { isActive, toggle };
	},
};
</script>
```

위와 같이 반응형 상태를 바인딩할 수 있습니다. <br>

그리고 active가 true이면 active가 클래스에 바인딩되고, <br>
false이면, 바인딩되지 않습니다. 그리고 false이면, 지워집니다. <br>
(참고로 버튼을 누르면, true와 false가 바뀝니다.)
<br><br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/06470a1d-d8a2-44eb-afd1-ae24b5aec578/image.png">
</div>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/857e0128-5f60-4098-a14d-bab9da2d3bf5/image.png">
</div>

<br>

그리고 다른 속성과 다르게  HTML 속성과 `v-bind` 디렉티브는 공존할 수 있습니다. <br>

```
<div class="text" :class="{ active: isActive }">텍스트입니다.</div>
```

위와 같이 선언했을 때, <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/7626fce0-f24c-40d8-ad9e-22cd1bde4e74/image.png">
</div>

이렇게 함께 공존하는 것을 확인할 수 있습니다. <br><br>

만약에 여러 개의 값을 넣어야한다면, 콤마를 사용할 수 있습니다. <br>

```
<div class="text" :class="{ active: isActive, text-danger }">
```

이렇게 되어있을 때, text-danger은 중간에 특수문자가 있으므로, 홑따옴표로 감싸줍니다.

```
<template>
  <div class="text" :class="{ active: isActive, 'text-danger': hasError }">
  ...
  <button v-on:click="hasError = !hasError">toggleError</button>
</template>

<script>
  const hasError = ref(false);
</script>

<style scoped>
  .text-danger {
      color: red;
  }
<style>
```

위의 코드는 'text-danger' 와 관련되어 수정된 내용입니다. <br><br><br>


만약에 바인딩할 데이터가 많다면, inline으로 사용하지 않고, object로 선언해서 사용할 수 있습니다.<br>

```
<div class="text" :class="classObject">
			<!--  오브젝트로 선언 -->
			
		---
		
		const classObject = reactive({
			active: true,
			'text-danger': false,
		});
		
		---
		
		return { classObject };		
```

위의 코드처럼 active가 true이고, text-danger이 false라면, <br>
다음과 같이 나옵니다.


<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/3a58885b-dcd4-47d4-b50e-cb7f0aa7d6d5/image.png">
</div>


<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/8da67c10-e20e-49ed-a8ed-ac19104c3d19/image.png">
</div>

반면, <br>
`'text-danger': false,`을 true로 바꾸면..<br>
다음과 같이 됩니다. <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/cfa43baf-abfb-488a-afa3-8709285dda14/image.png">
</div>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/1a8df5cd-a9c3-4a17-a33e-b4452ac89208/image.png">
</div>

만약, <br>
active 되는 상태가 여러 개가 필요하면, computed를 활용하면 조금 더 효율적입니다.<br>
다음과 같이 할 수 있습니다.

```
const classObject = computed(() => {
			return {
				active: true,
				'text-danger': true,
			};
		});
```

만약 조건이 여러 개 필요하다면, 다음과 같이 할 수 있습니다. <br>

```
const classObject = computed(() => {
			return {
				active: true && true,
				'text-danger': true && true,
			};
		});
```

혹은 클래스가 많이 필요할 수도 있습니다. <br>
다음과 같이 배열로 선언하시면 됩니다.

```
	<div class="text" :class="{ classObject, activeClass, errorClass }">
	
	---
	
        const classObject = computed(() => {
        return {
            active: true && true,
            'text-danger': true && true,
          };
		});

		const activeClass = ref('active');
		const errorClass = ref('error');
```

결과는 다음과 같습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/254bd0af-7e76-463f-a4bb-c52f82d3eba0/image.png">
</div>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/ff391416-76b0-4f5a-84aa-2ba49f29faad/image.png">
</div>

그리고 배열 안에 자바스크립트 표현식도 넣을 수 있습니다. <br>

```
<div
			class="text"
			:class="[isActive ? 'active-class' : 'class', errorClass]"
		>
			텍스트입니다.
		</div>
```

acitve가 true이므로 결과는 다음과 같습니다. <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/8c4b9752-80de-4db6-812e-11ae49627973/image.png">
</div>

혹여 속성을 더 추가하고 싶을 때, 
클래스에 속성을 더 추가하면 됩니다.

```
		const classObject = computed(() => {
			return {
				active: true && true,
				'text-danger': true && true,
				'text-blue': true, // 추가한 속성
			};
		});

---

        <div
			class="text"
			:class="[isActive ? 'active-class' : 'class', errorClass, classObject]"
		>
			텍스트입니다.
		</div>

```

이렇게 하면 됩니다.
<br><br>

이제 inline-styling을 바인딩하는 방법을 알아보도록 하겠습니다.
<br> 
div태그 에 lorem 탭을 누르면, 다음과 같이 됩니다.

```
<div :style="{}">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Deleniti laborum
			quos veniam. Assumenda, consequatur cumque dicta dignissimos eos et
			impedit in iste laudantium maiores maxime modi reiciendis repellat tempore
			voluptatem!
		</div>
```

그리고 div 태그 내의 `:style="{}"`처럼 클래스나 객체나 배열로 바인딩할 수 있습니다. <br>
<br>
다음과 같이 해보면,

```
const styleObject = reactive({
			color: 'red',
			fontSize: '13px',
		});
		return {
			styleObject,
		};
		
		...
		
		<템플릿>
		<div :style="styleObject">
		...
		
```

이와 같이 코드가 있을 때, <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/9ee2f33d-c826-4018-b273-4071ed573a0f/image.png">
</div>

이처럼 style이 적용된 것을 알 수 있습니다. <br>

> 참고로 CSS의 스타일 적용시 속성명을 넣을 때는 카멜케이스를 일반적으로 넣습니다.

폰트사이즈를 정해서 버튼 두개로 폰트를 조정하도록 해보겠습니다.<br><br>

```
    	<button v-on:click="fontSize--">-</button>
		<button v-on:click="fontSize++">+</button>

...

		const fontSize = ref(13);
		const styleObject = computed(() => {
			return {
				color: 'red',
				fontSize: fontSize.value + 'px',
			};
		});

		return {
			styleObject,
			fontSize,
		};
```

위와 같이 코드가 있을 때,

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/aea12a00-1b06-477f-95d3-236cbbd4c656/image.png">
</div>ㄴ

이렇게 나오는데, `+` 버튼을 3번 눌러보겠습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/38ea5110-81be-46ab-8005-7a13d4cdfcc1/image.png">
</div>

현재 16이기때문에, 7번을 `-`를 눌러 보겠습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/55a66ad2-e218-4e35-9739-9ae52ce5e83a/image.png">
</div>

이처럼 지금까지 class와 style에 바인딩하는 법을 알아보았습니다.

</details>

<details>
<summary>조건부 렌더링 (v-if, v-show)</summary>

### v-if

특정 조건에 따라 렌더링 여부를 결정할 때는 `v-if` 디렉티브를 사용합니다.<br>
`v-if`는 렌더링 조건을 결정할 수 있습니다. <br>
자바스크립트 표현식과 매우 유사합니다.<br>
만약, 조건식이 맞으면 출력되고, 조건식이 거짓이면, 출력되지 않습니다.<br>
<br>
그리고 if, else, else-if가 있듯이, `v-else`, `v-else-if` 가 있습니다.

```
<h2 v-if="visible">Hello Vue3!</h2>

...
	const visible = ref(true);
		return { visible };

```

위와 같은 코드가 있을 때,

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/1c9a8e8d-6a04-429f-8735-a859bdff8e5a/image.png">
</div>

`v-if`의 조건식이 true이기 때문에, h2가 렌더링 된 것을 확인할 수 있습니다.<br>
만약 위의 코드에서 ref 내부의 `true`를 `false`로 줬다면, 렌더링 되지 않습니다. <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/3fe0db86-b3ae-40d1-ac74-88940403ed09/image.png">
</div>

주석처리가 되어있네요. <br>
`v-if`는 false일 때 렌더링조차 되지 않는 것을 확인할 수 있습니다.<br><br>

```
		<h2 v-if="visible">Hello Vue3!</h2>
		<h2 v-else>false 입니다.</h2>
		<button v-on:click="visible = !visible">toggle</button>
```

이렇게 하면, 토글을 클릭하면 visible의 값이 바껴서 출력문자가 바뀝니다. <br><br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/a90d5511-074b-46c3-b6bd-e4ad9b2a0793/image.png">
</div>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/0c8bd3d9-bab8-493d-a853-c353ed2821ac/image.png">
</div>

`v-else-if` 예시도 보겠습니다.

```
<button v-on:click="type = 'A'">A</button>
<button v-on:click="type = 'B'">B</button>
<button v-on:click="type = 'C'">C</button>
<button v-on:click="type = 'D'">D</button>
<h2 v-if="type === 'A'">A입니다.</h2>
<h2 v-else-if="type === 'B'">B입니다.</h2>
<h2 v-else-if="type === 'C'">C입니다.</h2>
<h2 v-else>A, B, C가 아닙니다.</h2>
		
  ---
const type = ref('A');
return { type };
  
```

위와 같은 코드가 있을 때 결과는 다음과 같습니다.<br><br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/6d886265-3054-4898-9237-7b82ee0a6519/image.png">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/6a18e3ec-d66c-43f5-ab25-897d6e0db12f/image.png">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/3a395403-a4f1-4536-929f-8dc07efec89e/image.png">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/8702935e-5b30-4984-9ffa-f18270d1285d/image.png">
</div>

만약 여러 개의 HTML 요소를 `v-if` 디렉티브 하나의 조건으로 렌더링을 하고 싶다면, <br>
<template> 를 사용할 수 있습니다. <br>
다음 코드를 복사해서 붙여넣습니다.

```
<template v-if="visible">
  <h1>Title</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</template>
```

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/dc843cde-3947-4981-90a5-139d98e79ccf/image.png">
</div>

다음과 같이 하면 됩니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/3033a780-1881-4f68-b30e-657383b1b997/image.png">
</div>

화면상, `visible`이 현재 false이기 때문에, <br>
아무것도 출력되지 않지만, toggle을 눌러 true로 바꿔주면, 다음과 같이 렌더링 됩니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/48226c83-0506-43e6-8e4c-a412ceba6050/image.png">
</div>

템플릿으로 조건을 거는 것은 실무에서도 자주 쓰입니다.^^
<br><br>

`v-show` 디렉티브로 특정 조건의 렌더링 여부를 결정할 수 있습니다.<br>
이 디렉티브는 `else` 같은 건 없습니다.<br> 그냥 v-show만 있습니다.

```
<h1 v-show="ok">Title입니다.</h1>
<button v-on:click="ok = !ok">show toggle</button>

const ok = ref(true);
return {  ok };

```

위와 같은 코드가 있다고 했을 때, <br>

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/de0b7e6f-e380-448b-8e44-efda1d31e2b6/image.png">
</div>

처음 ok값이 true이므로 위와 같이 나오는 것을 확인할 수 있습니다.<br>
그리고 show toggle을 눌러보면, 다음처럼 나오지 않습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/117813f1-3c8c-4d6a-a092-fe32c1fe6814/image.png">
</div>

UI적으로는 `v-if`와 동일하지만, `v-if`는 아까 본 것처럼 html 소스에선 주석처리를 했다면, <br>
`v-show`는 html요소는 나옵니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/9477c79d-2b69-4909-b535-2fdae7f37e08/image.png">
</div>

style에 표시여부가 **none**임을 확인할 수 있습니다.<br>
이는 `v-show`와 `v-if`의 차이입니다.

#### v-if
- `v-if`는 실제로 렌더링 됩니다. 
  - 전환할 때 블록 내부의 컴포넌트들이 제거되고, 다시 생성됩니다.
- `v-if`는지연됩니다. 
  - 초기 렌더링시 조건이 거짓이면, 아무 작업도 하지 않습니다. 즉, 조건부 블록은 조건이 처음으로 참이 될 때까지 렌더링되지 않습니다.

#### v-show
- 엘리먼트는 CSS 기반 전환으로 초기 조건과 관계 없이 항상 렌더링됩니다.
- v-show는 DOM에 일단 우선 렌더링하고, 조건에 따라 CSS의 display의 block, display, none 속성으로 전환됩니다.

#### v-if VS v-show
v-if는 전환 비율이 높은 반면, <br>
v-show는 초기 렌더링 비용이 높습니다. <br><br>

따라서, 자주 전환해야 한다면, `v-show`를, 런타임시 조건이 변경되지 않는다면, `v-if`를 사용하는 게 좋습니다.

> 참고로 `v-if`와 `v-for`를 같이 사용하지 않느 것을 권장하고 있습니다.

</details>

<details>
<summary>목록 렌더링 (v-for)</summary>

### v-for
목록을 렌더링할 때 `v-for` 디렉티브를 사용할 수 있습니다.

```
const items = reactive([
  { id: 1, message: 'Java' },
  { id: 2, message: 'HTML' },
  { id: 3, message: 'CSS' },
  { id: 4, message: 'JavaScript' },
]);

<li v-for="(item, index) in items" :key="item.id">
  {{ item.message }}
</li> 
```

위과 같은 코드가 있을 때, <br>

`v-for=”item in items”` 에서 `items`라는 배열의 요소들을 `item`이라는 변수에 할당합니다. <br>
`v-for=”(item, index) in items”` 라는 문법을 사용해서 배열의 요소와 인덱스를 가져올 수 있습니다.<br>
항목을 나열할 때 각 :key 속성에는 고유한 값을 지정해야 합니다. (vue 2.2.0 부터 필수)

> key속성에 대해 궁금한 분들은 공식 홈페이지에서 다 자세하게 찾아보시면 될 거 같습니다.

```
<li v-for="(item, index) in items" :key="item.id">
  {{ item.message }}
</li> 
```

위으 코드에서 `item.message`를 `item`이라고 바꾸면, 다음과 같이 출력됩니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/9da6e523-cfc4-4cb8-8d06-f7d21a647e3a/image.png">
</div>

`item.message`로 하면 다음과 같습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/2f0ecfcc-30b5-46d2-b55b-1637a1fc7801/image.png">
</div>

그리고 아래와 같은 경고창이 뜰 때, :key 속성에 아래의 코드와 같이 고유한 값을 주면 됩니다. <br>

```
<li v-for="item in items" :key="item.id">
```

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/f73651da-8286-4c44-83d0-6a4b51dfc3f6/image.png">
</div>

<br>

인덱스는 다음과 같이 사용하면 됩니다.

```
인덱스: {{ index }},{{ item.message }}
```

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/8dd083bd-a656-471f-affd-bc34c095427f/image.png">
</div>

이렇게 출력되는 것을 확인할 수 있습니다.<br><br>

아이디가 짝수인 것만 출력해보도록 하겠습니다.

v-for와 v-if를 함께 사용하지 않는 것을 권장했는데,
이때는 template로 감싸서 사용하시면 됩니다.

```
<template v-for="(item, index) in items" :key="item.id">
    <li v-if="item.id % 2 === 0">
        ID: {{ item.id }} 인덱스: {{ index }},{{ item.message }}
    </li>
</template>
```

결과는 다음과 같습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/e75582f9-91c7-4d4f-9b1a-f9f3b5c970f8/image.png">
</div>

computed를 활용할 수도 있습니다.

```
const evenItems = computed(() => items.filter(item => item.id % 2 === 0));
```

Array API를 이용해서 짝수인 것만을 이용하여 출력합니다.

```
<template v-for="(item, index) in evenItems" :key="item.id">
  <!--				<li v-if="item.id % 2 === 0">-->
  <li>ID: {{ item.id }} 인덱스: {{ index }},{{ item.message }}</li>
</template>
```

template은 다음과 같이 합니다. <br><br>

객체를 `v-for`를 통해서 뿌려보도록 하겠습니다. <br>

```
<li v-for="(value, key, index) in myObject" :key="key">
    {{ key }}-{{ value }}-{{ index }}
</li>

---

  const myObject = reactive({
      title: '제목',
      author: '홍길동',
      publishedAt: '2023-11-17',
  });
```

이처럼 할 수 있습니다. <br>
key는 title, author, publishedAt이 될 것이고, <br>
value는 '제목','홍길동','2023-11-17'이 될 것입니다. <br><br>

결과는 다음과 같습니다.

<div align="left">
  <img src="https://velog.velcdn.com/images/tjdtn4484/post/376df94d-9908-42f9-9ab1-0195d0743b01/image.png">
</div>

</details>
