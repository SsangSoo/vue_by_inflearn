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
