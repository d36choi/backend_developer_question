## vue 의 라이프 사이클을 설명하라
vue2 기준, vue3 는 다름. 더 세분화 
- beforeCreate : 아직 data와 events(vm.$on, vm.$once, vm.$off, vm.$emit)가 세팅되지 않은 시점  
- created : 이제 data와 events가 활성화되어 접근할 수 있다
- beforeMount
- mounted : rendering 이후라서 DOM 에 접근 가능. 자식의 mounted 가 먼저 동작함
- beforeUpdate
- updated : 반응형 속성이 변경되어 재 렌더링 되고 접근
```
    this.$nextTick(function () {
      // 모든 화면이 렌더링된 후 실행합니다.
    })
```
- beforeDestroy
- destroyed

## VueJS 를 사용하는 이유가 뭘까요?

개발 생산성, 자동 프로젝트 생성이 용이함

- **Virtual DOM**: ReactJS 같은 가상 DOM 을 사용합니다. HTML DOM 의 경량화 인메모리 트리입니다. 오리지널 DOM 이 자꾸 업데이트되면 브라우저 처리 연산이 많아집니다.
그러면 브라우저의 DOM 렌더링이 느려지고 사용자 경험이 저하됩니다.  
- **Components**: 재사용가능한 컴포넌트를 만들어서 개발 속도가 빨라집니다.
- **Templates**: Vue.js는 렌더링 된 DOM을 기본 Vue 인스턴스의 데이터에 선언적으로 바인딩 할 수있는 HTML 기반 템플릿 구문을 사용합니다. 모든 Vue.js 템플릿은 스펙을 호환하는 브라우저 및 HTML 파서로 구문 분석 할 수있는 유효한 HTML입니다.  
- **Routing**: vue-router 를 이용한 편리한 라우팅 기능 구현  
- **Light weight**: 다른 프레임워크에 비해 가볍다.  

[Vue 를 사용하게 된 이유](https://pinokio0702.tistory.com/363)

## vue3 , vue2 의 차이점
[vue3 변경점 정리](https://velog.io/@bluestragglr/Vue3-%EB%AC%B4%EC%97%87%EC%9D%B4-%EB%B0%94%EB%80%8C%EB%82%98%EC%9A%94)

[vue 2](https://medium.com/witinweb/vue-js-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-7780cdd97dd4)
