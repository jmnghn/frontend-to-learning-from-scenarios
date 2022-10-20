## Step1. 개발

```
1. 가장 중요한 것
2. 개발자가 채겨야 하는 것
3. web1
```

### 가장 중요한 것

"개발할 때 중요한 것은 무엇인가요?"(개방형 질문 😅)<br />

eg. 보통 이야기하는 중요한 것<br />

- 애플리케이션 아키텍처
- 시스템 아키텍처
- 프로그래밍 테크닉, SOLID...
- 일정, 안정성, 확장성, 유연성...

개인적으로 중요하다고 생각하는 것 ⭐️<br />

- 자산(시간, 사람, 기술력 등) 인지 기반 활동<br />
  항상 내가 가지고있는 자산을 바탕으로 플래닝하는 훈련을 해라. (주먹구구식 플래닝을 하는 개발자들이 너무 많다. 🥲)
- 이슈에 대한 선제적 커뮤니케이션<br />
  이슈가 생겼을 때, 빨리 커뮤니케이션 하는 게 중요하다. 그리고 시간을 들여서 해결했다고 하더라도 그것이 능력으로 평가받는다고 생각한다면 큰 오산이다. ^^; 팀 활동에 있어서 굉장히 중요하지 않고 또 전체적으로 플래닝을 다 망가뜨릴 수 있는 요소로 작용하니까. "부끄러워하지 말고 꼭 드러내라."는 조언. 하지만, 무조건 모든 걸 다 이슈라고 드러내는건 당연히 안된다. 반드시 내가 어느정도 리미트(!)를 걸어놓고, 그 결과를 가지고 이슈레이징을 해야 한다.
- 개발자가 챙길 수 있는 것 챙기기
- 지속적인 진행 상황 가시화<br />
  진행 상황을 최대한 자주, 언제든 확인할 수 있는 방법을 만들어 놓는 것. (제품의 진행 상황, task의 진행 상황 이든...) 언제나 가시화하고 언제나 누구나 볼 수 있는 상황을 만들어 놓는 것이 굉장히 중요하다.<br />
  예로, 한달 반짜리 프로젝트. 한달 뒤에 '짜잔~'... 무수히 많은 문제들이 있는 케이스들이 많은데 (^^;) 절대로 이러면 안된다.

<br />

### 개발자가 챙길 수 있는 것

- 테스트 - 단위 테스트 vs. E2E 테스트
- 로그 - 사용자 로그, 앱 로그
- 예외 상황 처리 - 404, 500, etc...
- 코드에 매몰되지 않기 <br />
  물론 중요하지만, 좋은 코드와 좋은 아키텍처가 좋은 제품이나 좋은 서비스가 되기 위한 필수조건은 아니다.<br />
  좋은 서비스 혹은 나쁜 서비스와 좋은 코드 그리고 아키텍처와는 인과관계가 맞지 않을 수 있다. 😅 이와같은 측면에서 언제나 첫 번째 우선순위는 '제품'이다.<br />
  '제품'이 잘 딜리버리 되는 것. 그 '가치'를 만들어내는데 필요한 것들이 동작하는 것이 언제나 제일 첫 번째의 가치다.<br />
  이런 것들을 잘 운용하기 위한 두 번째 가치가 바로 좋은 코드, 좋은 아키텍처 등등이 되는 것이다. 그래서 코드나 아키텍처에 너무 매몰되지 않아야 하겠다는 것을 늘 자각하기. (엉뚱한 곳에 시간쓰는 사람들을 너무 많이 보게된다.)

#### daily refactoring

"리팩토링을 해야 한다." 이런 이야기들을 많이 한다.<br />
"이 코드가 이러이러한 것들을 하면서 이러이러한 것들의 문제점들... 즉, 레거시화 되어서 이걸 리팩토링 해야 돼요. 그러지 않으면 여러가지 문제들이 생겨요. ㅠㅠ"...<br />
이런 이야기를 하는 개발자들이 많이 있다. 우리는 이런 이야기를 하는 개발자가 되지 않았으면 좋겠다.<br />
어떤 이야기냐면, "daily refactoring".<br />
즉, 리팩토링은 개발자가 본래 개발자로서 매일매일 해야하는 원래 '일'이다. 개발이라고 하는 거에 포함되어 있는 '일'이다.<br />
굳이 리팩토링을 다른 사람한테 "리팩토링 해야하는데, 해도 돼요?", "안해도 돼요?"와 같은 이야기를 한다는 것 자체가 말이 안 되는 이야기다.<br />
마치 나는 제품을 개발하는 개발자인데 "제품을 개발해도 돼요?", "안해도 돼요?"와 같이 물어보는 것과 똑같은 상황처럼 느껴진다.<br />
이런 이야기를 하는 이유는 "리팩토링 해야하는데 해도 돼요?", "기간을 좀 따로 주시면 안돼요?", "시간을 좀 주시면 안 돼요?" 와 같은 이야기를 하는 개발자들이 생각보다 많기 때문이다.<br />

...우리는 이런 이야기를 하는 개발자가 안 됐으면 좋겠다. 리팩토링은 그냥 개발의 일부인 것이다.<br />
언제나 부지불식간에 매일매일 리팩토링 되어야 하는 것이다.<br />
우리가 고민해야 할 것은 "엔지니어링 측면에서 매일매일 리팩토링 하려면 어떤 부분들이 전제가 되어야 할까?"를 고민하는 게 우리의 역할이지, 리팩토링을 하기 위해서 시간도 필요하고 따로 스케줄링 해야 되고, 어떤 사람이나 조직의 허가가 있어야 되고... 이런 생각을 하면 안된다라는 거~😅!

<br />

### web1

`/web/web1`<br />

`web1`을 실행시키기 위해 필요한 여러 가지(!)들...<br />
docker의 mysql을 실행시켜야 하고, 두 개의 서버를 실행 시켜야 하고...(b2b-server와 cdn)<br />

```json
// /web/web1의 package.json
"scripts": {
    "dev:all": "concurrently --kill-others \"npm run dev\" \"npm run css\"", // tailwindcss의 프로세스와 nextjs를 실행하는 프로세스, 2개의 프로세스를 모두 실행하기 위한 명령어
    "dev": "RUNTIME=develop next dev -p 1203",
    "dev:prod": "RUNTIME=prod next dev -p 1203",
    "css": "tailwindcss -i ./css/main.css -o ./public/css/default.css --watch",
    "test": "cypress open",
    "build": "next build",
    "start": "RUNTIME=prod next start -p 1203",
    "lint": "next lint"
  },
// ...
```

멀티 configuration...:) <br />

> 다양한 방법들이 있고, 차후에 이런 dependency까지 제거하면서, `remote-config`형식으로 개발하는 `/backend/remote-config/`를 다룬다.<br />
> 한 곳에서만 설정을 관리하고 변경 시 여러개의 web 프로젝트들에 함께 적용할 수 있는!

`/web/config/index.js`

```js
import commonConfig from "./config.common";
import developConfig from "./config.develop";
import prodConfig from "./config.prod";

export default process.env.RUNTIME === "prod"
  ? { ...commonConfig, ...prodConfig }
  : { ...commonConfig, ...developConfig };
```

`/web/config/config.develop.js`

```js
const config = {
  server: {
    b2c: "http://api.12shop.com:1202",
    cdn: "http://cdn.12shop.com:1201",
  },
};

export default config;
```

`/web/config/config.common.js`

```js
const config = {
  metadata: {
    title: "12shop",
  },
};

export default config;
```

`/web/config/config.prod.js`

```js
const config = {
  server: {
    b2c: "https://api.12shop.com",
    cdn: "https://cdn.12shop.com",
  },
};

export default config;
```

- `_document.js`의 `<Head />`와 페이지 내부의 `<Head />`, `_app.js`의 `<Head />`의 적절성.
- `<ErrorBoundary>` 컴포넌트 디자인 패턴. (전역)
- 외 404, 500 페이지
- 앱 로그(sentry) - 로그가 없으면, 우리는 까막눈 3.3)
- 테스트(cypress)
