### Getting started with Next.js

#### Installing Next

From [Getting started with next.js](https://nextjs.org/learn/foundations/from-react-to-nextjs/getting-started-with-nextjs)

Next gives us many things out of the box:

- Next.js will create html and body for you
- Jsx compiler
- Etc...

```js
// package.json
{
}
```

```bash
# Install
npm install react react-dom next.js
```

```js
// package.json
{
  "dependencies": {
    "next": "^13.2.4",
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  }
}
```

```js
// Add dev script to package.json
{
  "scripts": {
    "dev": "next dev"
  },
  "dependencies": {
    "next": "^13.2.4",
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  }
}
```

```js
// Add basic index.js script to a pages-directory, NOTE: Use export default for root app to render
import { useState } from "react";
function Header({ title }) {
  return <h1>{title ? title : "Default title"}</h1>;
}

export default function HomePage() {
  const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"];

  const [likes, setLikes] = useState(0);

  function handleClick() {
    setLikes(likes + 1);
  }

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>

      <button onClick={handleClick}>Like ({likes})</button>
    </div>
  );
}
```

```bash
# Run dev
npm run dev
```
