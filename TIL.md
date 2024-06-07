Next.js SetUP

- NextJS는 실행할 때 APP 폴더 안의 page라는 파일을 찾는다.

app 폴더 아래에 폴더를 생성하면 그 폴더는 페이지가 될 수 있음을 암시한다.

- 폴더 안에 pages 파일을 생성하면 UI가 렌더링된다.
- 폴더 안에 pages 파일이 없다면 경로로 취급되지 않는다.

Rendering

- NextJS가 리액트 컴포넌트를 브라우저가 이해할 수 있는 HTML로 변환하는 작업

CSR

- 모든 렌더링이 클라이언트 측에서 발생한다.
- 클라이언트는 자바스크립트를 로드하고, 자바스크립트가 UI를 빌드한다.

SSR

- server(backend)에서 rendering을 한 후 application을 render한다.
- NextJS로 웹 사이트를 빌드할 때, 기본적으로 SSR을 사용한다.

Hydration

- SSR(서버사이드 렌더링)을 통해 만들어진 정적인 HTML을 클라이언트측 자바스크립트를 사용하여 동적인 리액트 컴포넌트로 변환하는 과정이다.
  - 서버 환경에서 이미 랜더링 된 HTML에 React를 추가한다 생각
- NextJS는 컴포넌트롤 정적인 HTML로 변환 후 사용자에게 제공한다.
- 사용자에게 제공한 후 프레임워크가 로드되면 정적인 HTML을 동적인 HTML로 변경한다.

Client Components

- 클라이언트 컴포넌트를 사용하기 위해 파일 상단데 "use client"를 명시한다.
- use client를 명시하게 되면 동적인 렌더링이 가능해진다.
  - 즉, 상태 변화가 필요없는 component들은 use client를 명시할 필요가 없다.
    - ex) <h1>Title</h1> => Title은 변할 필요가 없음
    - ex) const [count, setCount] = useState(0) =? count가 변함에 따라 rerendering이 필요 => use client를 명시하여 동적인 렌더링 가능하게 명시
- backend에서 render되고 frontend에서 hydrate됨을 의미한다.
- use client를 선언하지 않으면 기본적으로 모두 server component이다.
  - use client와 server component 모두 server에서 render가 된다.
    - use client는 server에서 render된 후, hydrate된다.
    - server component는 server에서 render된 후, hydrate되지 않는다.
