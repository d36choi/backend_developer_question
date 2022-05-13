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


## vue3 , vue2 의 차이점
[vue3 변경점 정리](https://velog.io/@bluestragglr/Vue3-%EB%AC%B4%EC%97%87%EC%9D%B4-%EB%B0%94%EB%80%8C%EB%82%98%EC%9A%94)

[vue 2](https://medium.com/witinweb/vue-js-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-7780cdd97dd4)
