---
title: React ネストされたリンクの設定
date: 2022-09-19 05:56:00
tags: react
---

{% plantuml %}

(*) --> "Find Event"
"Find Event" -> "Attend Event"

if "Capacity?" then
  ->[ok] "Create Ticket"
else
  -->[full] if "Standby?" then
    ->[ok] "Standby Ticket"
  else
    -->[no] "Cancel Ticket"
    "Cancel Ticket" --> (*)
  endif
endif

"Create Ticket" --> ==show==
"Standby Ticket" --> ==show==
==show== --> "Show Ticket"
"Show Ticket" --> (*)
{% endplantuml %}

```
\SRC
│  App.css
│  App.jsx
│  App.test.js
│  index.css
│  index.js
│  logo.svg
│  reportWebVitals.js
│  setupTests.js
│
├─components
│      Home.jsx
│      Page1.jsx
│      Page1DetailA.jsx
│      Page1DetailB.jsx
│      Page2.jsx
│
└─router
        Router.jsx
```

package.json
```json
  "dependencies": {
    "@testing-library/jest-dom": "^5.16.5",
    "@testing-library/react": "^13.4.0",
    "@testing-library/user-event": "^13.5.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.3.0",
    "react-scripts": "5.0.1",
    "web-vitals": "^2.1.4"
  },
```

```js
import { BrowserRouter, Link } from 'react-router-dom';
import './App.css';
import { Router } from './router/Router';

const App = () => {
  return (
    <BrowserRouter>
      <div className="App">
        <Link to={`/`}>Home</Link>
        <br />
        <Link to={`page1`}>Page1</Link>
        <br />
        <Link to={`page2`}>Page2</Link>
      </div>
      <Router />
    </BrowserRouter>
  );
}

export default App;
```

```js
import { Routes, Route } from "react-router-dom";
import { Home } from "../components/Home";
import { Page1 } from "../components/Page1";
import { Page1DetailA } from "../components/Page1DetailA";
import { Page1DetailB } from "../components/Page1DetailB";
import { Page2 } from "../components/Page2";

export const Router = () => {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="page1">
        <Route index={true} element={<Page1 />} />
        <Route path={`detailA`} element={<Page1DetailA />} />
        <Route path={`detailB`} element={<Page1DetailB />} />
      </Route>
      <Route path={`page2`} element={<Page2 />} />
    </Routes>
  );
}
```


```js
import { Routes, Route } from "react-router-dom";
import { Home } from "../components/Home";
import { Page1 } from "../components/Page1";
import { Page1DetailA } from "../components/Page1DetailA";
import { Page1DetailB } from "../components/Page1DetailB";
import { Page2 } from "../components/Page2";

export const Router = () => {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="page1" element={<Page1 />}>
        <Route path={`detailA`} element={<Page1DetailA />} />
        <Route path={`detailB`} element={<Page1DetailB />} />
      </Route>
      <Route path={`page2`} element={<Page2 />} />
    </Routes>
  );
}
```
