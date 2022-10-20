## SSR PoC

```
1. Setup
2. PoC 계획과 목표
3. 지름길
4. npm start
```

### Setup

#### On Database

도커에서 이전에 받았던 mysql:latest 이미지 실행.
(Containers 탭에서 mysql container, START 버튼 클릭해 실행)

`/bootstrap/mysql/database-init.sql`에 CREATE 문~

`12shop` 데이터베이스 만들기 :)

<br />

#### Run API Server

`/backend/b2b-server`

```
npm install
npm start run:init # TypeORM으로 테이블 생성
npm start run:debug
```

<br />

#### Run CDN

`/backend/cdn`

<br />

#### Create Dummy Data

`/bootstrap/mysql/database-init.sql`에 Insert문~ (products, product-photos)

#### Request Test Call

`/step-by-step/poc-ssr-showcase/rest.http`

여기에서도 나오는 VS Code Extension! `REST Client`!

```
GET http://api.12shop.com:1202/products HTTP/1.1
```

<br />

### PoC 계획과 목표

#### "무엇을 확인할 것인가?"

확인할 목표를 정확하게 짚어 놓고. '그 범위 안에서' 우리가 받은 쓸 수 있는 시간 안에 실행하는 것.
거기서 최적의 정보를 뽑아내는 것이 항상 중요하다.<br />
(※ 일을 할 때, 항상 목표를 세우고 그 범주 안에서 일을 해야한다. <br />
그걸 하지 않으면, 막연하게 그리고 또 한없이 시간을 쓰고도 정작 길을 잃어버릴 수도 있는 일들이 굉장히 비일비재하다.)

<br />

#### 목표

- Next.js SSR 라우트 구조 확인
- 페이지별 Meta Taging <br />
  > 가능한지. 잘 되는지. 확인. <br />
  > 왜냐하면 SEO를 우리가 분석을 해봤을 때, 기술적인 측면에선 여러 가지 중요한 것들이 굉장히 많지만<br />
  > 핵심적인 것은 이 컨텐츠를 검색엔진한테 적절하게 잘 설명해 주는 것이다.<br />
  > 그래서 메타 태그를 잘 세팅하는 것이 중요했기 때문에 확인해볼 필요가 있다... :) (공유도 마찬가지)
- API Fetching <br />

  > 어플리케이션을 커다란 덩어리(!)로 구분지어 보자면 어떻게 구분지어 볼 수 있을까?<br /> `데이터`가 있고, 그 데이터를 `UI`로 만드는 로직이 있다. 그리고 클라이언트는 이름에서도 알 수 있듯이 스스로 데이터를 가지고 있지 않다.<br />
  > 그래서 대부분의 데이터를 remote에서 가져온다. 그렇지 않은 경우도 아주 가끔 있긴 하지만, 보통은 그 'remote'가 API 서버인 경우가 많고, 거기서 데이터를 가져오는 경우가 많다.<br />
  > 그렇기에 네트워크를 이용해서 데이터를 가져오는 `데이터 페칭(fetching)`이 굉장히 중요할 것이다.<br />
  > 데이터 fetching 로직... 여기엔 부수적으로 에러 처리나 예외 처리 등등 여러가지가 있다보니 데이터가 컸을 때 혹은 여러 가지의 API를 동시 다발적으로 호출해야 될 때와 같은 다양한 상황들에서 여러 가지 문제들이 생길 수 있으며, 또 '코드의 구조'를 어떻게 만드는지에 대한 고민들이 많이 들어가는 부분 가운데 하나다.<br /><br />
  > 이 데이터를 가져오는 일이 CSR은 굉장히 심플하다. 항상 remote 서버에 호출을 하는 상황 한 가지 뿐이다.<br /> 하지만, SSR은 서버에서 html 조각을 완성하는 일인데, 이 html 조각을 완성할 때 당연히 데이터가 필요한 일도 있다보니, 서버에서 'Fetching'이 일어나는 것과 클라이언트 사이드에서 API Fetching이 일어나는 상황. 즉, 두가지가 된다. 그리고 또 비동기적으로 호출되는 api특성 상 훨씬 더 복잡해질 수도 있는 상황 연출이 얼마든지 있을 수 있다. <br />
  > 그래서 이와 같은 맥락에서 API Fetching과 관련된 부분들을 잘 살펴보겠다는 관점의 항목이다. :) <br />

- Next.js 기능 목록 체크<br />
  > 위 3가지 정도를 확인하면, 큰 틀에서는 Next.js가 많이 쓰이고 레퍼런스도 많고 프로젝트의 개발과 그 커뮤니티도 굉장히 활성화 되어있다는 것을 알 수 있다. (^^;)<br />
  > 지금 아주 특별한 서비스를 개발하는 것은 아니니까 이 정도 측면에서면 충분해보이고 그럼에도 불구하고 어떤 기능들이 있는지 나머지 것들도 한번 살펴볼 필요성들이 존재한다.<br />
  > 그 중에 생각지 못한 유용한 것들이 있을 수 있으니까 :) (오... 저거 써먹어야겠다! 싶은 부분들이 있을 수 있으니까)<br /> <br />
  > 이와 같은 측면에서 기능 목록 체크를 한다는 의미... :)<br /><br />
  > 사실, 대부분의 개발자들이 공식 문서와 제공되는 기능 목록을 상세하게 잘 보지는 않는다.<br />
  > 다른 이유보다도 시간이 없기 때문이다...🥲🥲🥲 이런 부분을 상기시키고자 넣은 항목이고,<br />
  > 개발자로서 어떤 걸 먼저 봐야하고, 뭘 나중에 봐도 되는지를 잘 구분하고 분류하는 감각과 능력을 길러나가야 한다.<br />
  > (나중에 봐도 될거라고 생각한 부분에서 문제가 생길여지는 늘 있지만 🥲🥲🥲 그럼에도 불구하고 '의도적인 훈련'을 해야만 이런 능력들이 쌓여나갈 것이다.)

<br />

### POC 확인

#### 프로젝트 셋팅

`/step-by-step/Next-js-Boilerplate`

<br />

#### Next.js SSR 라우트 구조 확인

※ 여러개의 화면으로 이루어진. 즉, 'n개의 화면을 어떤식으로 전환하고 어떻게 데이터를 주고받는가.' '화면과 화면 간에 데이터 주고받기' 혹은 '전체 데이터를 확장을 하면서 어떻게 가져오는가' 와 같은 식의 구조를 파악하면 다 파악이 된 것 같은 기분이 든다. 개인적으로는 클라이언트 개발에 있어서 제일 핵심적인 부분으로 본다. 왠지, Routing에 대해서만 잘 알면 그 프로젝트에 대해 잘 알게 되는 것 같은 착각이 든다. ^^; <br />

[`File-system based router.`](https://nextjs.org/docs/routing/introduction)<br />

쉽네~ '굉장히` 직관적이내~ 별거 없내~ ...근데 뭐지... <br />
동물적인 불안감...🤔 <br />

- File-system routing
- Dynamic routing
- Shallow routing
- Routing & **Lifecycle** (라이프사이클이랑 맞물리면, 복잡해지겠는데...? 가뜩이나 SSR이라 클라이언트 비동기 통신이랑 서버 비동기 통신도 있는데...🤔)

<br />

#### 페이지별 Meta Taging

[`next/head`](https://nextjs.org/docs/api-reference/next/head)

<br />

#### API Fetching

- Server side
  - [getServerSideProps](https://nextjs.org/docs/basic-features/data-fetching/get-server-side-props)
  - [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching/get-static-props)
- [Client side](https://nextjs.org/docs/basic-features/data-fetching/client-side)<br />

  > ※ 근데 가만 생각해보면, Next.js는 SSR 프레임워크인데 굳이 CSR 데이터 페칭을 왜 다룰까? 문서 내용도 그렇고...<br />
  > (조금 더 내려보면 SWR이 있다. ㅋㅋ 😅)<br />

  문서를 보다가 새로운 게 (여기서는 SWR) 나와서 거기에 주의를 뺏기면 안된다. 적당히 살펴보고 RFC 참조 문서에 링크를 달기... ^^; <br />
  브레이크가. 있어야 한다. 🥲 그래야 일을 합리적으로 할 수 있다.

<br />

- API gateway

<br />

#### Next.js 기능 목록 체크

- [Image optimization](https://nextjs.org/docs/api-reference/next/image)
- Font optimization

<br />

### 지름길 (Next.js Boilerplate)

좋은 Boilerplate를 탐색해 살펴보기 [(Next-js-Boilerplate)](https://github.com/ixartz/Next-js-Boilerplate) <br />

`package.json`, `next-seo`, ... :)
