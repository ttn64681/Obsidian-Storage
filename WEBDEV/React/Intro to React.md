### JSX is syntactic sugar for creating html elements:
- Transpiles JSX to React.createElement

*// Using React.createElement*
_React.createElement('div', { className: 'container' },_ 
  _React.createElement('h1', null, 'Hello, world!')_
_);_
*// Using JSX*
<div className="container">
 <h1>Hello, world!</h1>
</div>

<hr>

### What is React?
- Front-end JS library for building component based UI
- reusable components makes it easier to build modular apps

### Why React?
- Popular - compatability
- Faster and easier to build apps
- 'Lightweight' - usually combined w/ React Router
	- component rerendering:
	- Uses virtual DOM to detect changes from real DOM and only updates that part of the real DOM
	- this is known as **reconciliation**



_import { useState } from 'react';_
_function SubmitButton() {_
   _const [isSubmitted, setIsSubmitted] = useState(false); // state hook_
	- 
   _function submitHandler() { // function to set to true_
      _setIsSubmitted(true);_
   _};_
   _return (_
      _<button onClick={submitHandler}> 
      { isSubmitted ? 'Loading…' : 'Submit' }
      </button>_
   _);_
_};_
_export default SubmitButton;_

- {} curly braces indicate to read as Javascript

```js
const articleTitle = "As We May Think";
const articleAuthor = "Vannevar Bush";
const readNumber = 750;

const articleJSX = (
  <article>
    <h1>{articleTitle}</h1>
    <p>by {articleAuthor}</p>
    <p>Read by {readNumber}</p>
  </article>
)
```

export default function App() {
  return <div> 
    <h1>Tour Stops</h1>
    <ul>
        <li>🇺🇸 New York City, US - Madison Square Garden</li>
        <li>🇬🇧 London, UK - Wembley Stadium</li>
        <li>🇩🇪 Munich, DE - Zenith Halle</li>
        <li>🇯🇵 Tokyo, JP - Budokan</li>
        <li>🇦🇺 Melbourne, AU - The Forum</li>
    </ul>
  
  </div>;
}

export default function App() {
  const barcelonaImage = <img src={"https://i.imgur.com/qaQNzqi.png"}  alt="Barcelona" />;
  const tokyoImage = <img src={"https://i.imgur.com/OAx1wzO.png"}  alt="Tokyo" />;
  const ohioImage = <img src={"https://i.imgur.com/CxJjltu.png"}  alt="Ohio" />;
  const imageGallery = [barcelonaImage, tokyoImage, ohioImage];
  const listItems = imageGallery.map((image) =>
    <li>{image}</li>
  );

  return (
    <ul>
      {listItems}
    </ul>
  );
}



  
