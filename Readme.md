# 개요

웹팩은 모던 js앱을 위한 정적 모듈 번들러죠.

웹팩이 앱을 처리할 땐, 프로젝트에 필요한 모든 모듈을 매핑하고 한 개 이상의 번들을 생성하는 의존성 그래프를 내부적으로 만듭니다.

> 자바스크립트 모듈과 웹팩 모듈에 대해 더 알고 싶다면 <a target="_blank" href="모듈.md">여기</a>를

4.0.0부터는 프로젝트를 번들하기 위한 설정 파일이 필요없지만, 요구사항에 더 잘 부합하도록 상세히 설정할 수도 있습니다.

핵심 개념만 이해하면 시작할 수 있습니다.

* 엔트리(Entry)
* 아웃풋(Output)
* 로더(Loaders)
* 플러그인(Plugins)
* 모드(Mode)
* 브라우저호환성(Browser Compatibility)

이 문서는 위 개념에 대한 이해와 개념에 대한 구체적인 사례 및 링크를 제공합니다.
하지만 모듈을 번들하고 내부에서 어떻게 작동하는가에 대한 기초 개념이 궁금하면 아래 링크를 참고하세요.

<a target="_blank" href="https://www.youtube.com/watch?v=UNMkLHzofQI">앱 수동 빌드</a>
<a target="_blank" href="https://www.youtube.com/watch?v=Gc9-7PBqOC8">간단한 모듈 번들러 라이브코딩</a>
<a target="_blank" href="https://github.com/ronami/minipack">간단한 모듈 번들러의 상세한 설명</a>

## 엔트리(Entry)
진입점은 웹팩 모듈이 쓰게 될 내부의 의존성 그래프를 만들기 위해 필요합니다. 웹팩은 진입점을 통해 직간접적으로 의존하는 모듈과 라이브러리를 파악합니다.

기본값은 ./src/index.js고 webpack.config.js 파일로 entry를 지정하여 다른 진입점을 구성할 수 있습니다. 진입점을 여러 개로 구성하는 것도 가능합니다.

> 역주: 진입점은 c나 java의 main함수처럼 최초 시스템이 부르게 되는 함수(여기서는 파일)을 말합니다. 웹팩은 이 파일로부터 차근차근 의존하는 모듈과 라이브러리를 검색해가며 파악합니다.

```js
module.exports = {
  entry: './path/to/my/entry/file.js'
};
```

> 더 자세한 정보는 <a target="_blank" href="엔트리포인트.md">엔트리포인트</a>로

## 아웃풋(Output)

## 로더(Loaders)

## 플러그인(Plugins)

## 모드(Mode)

## 브라우저호환성(Browser Compatibility)
