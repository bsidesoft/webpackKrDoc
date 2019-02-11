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
아웃풋은 웹팩이 생성한 번들의 저장할 위치와 이름을 알려줍니다. 기본값은 ./dist/main.js고 다른 파일이 생성되는 경우는 ./dist폴더입니다.

webpack.config.js 파일로 output를 별도로 지정할 수 있습니다.

```js
const path = require('path');

module.exports = {
  entry: './path/to/my/entry/file.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'my-first-webpack.bundle.js'
  }
};
```

위 코드에서 output.filename과 output.path을 이용해 번들의 위치와 이름을 지정합니다(path는 nodejs의 모듈입니다)

> 역주: output의 경로는 반드시 완전한 절대 경로여야 합니다.

> 더 자세한 정보는 <a target="_blank" href="아웃풋.md">아웃풋</a>으로

## 로더(Loaders)
웹팩은 오직 js와 json만 이해할 수 있습니다. 로더를 사용하면 다른 형식의 파일을 의존성 그래프에 추가할 수 있게 변환하여 앱에서 사용할 수 있게 처리합니다.

> 어떤 모듈(예를 들면 .css파일)은 웹팩에서 임포트하는 사양이므로 다른 번들러나 태스크 러너에서 지원 안될 수도 있습니다. 로더는 보다 정확한 의존성 그래프를 만들도록 해줍니다.

크게 보면 웹팩 설정 상 로더는 두 가지 속성을 갖습니다.

* test속성은 변환할 파일을 식별합니다.
* use속성은 변형을 수행하기 위해 사용할 로더를 가리킵니다.

webpack.config.js

```js
const path = require('path');

module.exports = {
  output: {
    filename: 'my-first-webpack.bundle.js'
  },
  module: {
    rules: [
      { test: /\.txt$/, use: 'raw-loader' }
    ]
  }
};
```

위 설정에서 단일 모듈에 test, use속성을 갖는 rules속성을 정의했습니다. 이는 웹팩에게 다음과 같이 컴파일하라고 지시한 것입니다.

"require()나 import 문에 '.txt'를 포함하는 경로가 발견되면 번들에 추가하기 전에 먼저 raw-loader를 사용해 변형해라"

> 웹팩에서 rules를 정의할 때는 rules가 아니라 module.rules에 정의합니다. 잘못된 키로 지정하면 웹팩은 경고합니다.

> test속성에서 정규식 매칭에는 따옴표를 쓰지 않습니다. 직접 따옴표로 지정하는 경우와 정규식으로 지정하는 경우의 차이에 유의하세요.

> 더 자세한 정보는 <a target="_blank" href="로더.md">로더</a>로

## 플러그인(Plugins)

## 모드(Mode)

## 브라우저호환성(Browser Compatibility)
