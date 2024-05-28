# Virtual and Shadow DOM

In ReactJS, virtual DOM is a copy or blueprint of real/actual DOM.

Imagine if we are rearranging furniture in a room. Instead of moving each piece one by one, we sketch out the changes first (virtual DOM), figure out the most efficient way to move things around, and then make the actual changes (actual DOM). This can saves time and effort because we are only making the necessary changes, rather than redoing everything from scratch.

Suppose we have a simple React component that displays a list of items:

```js

// React component
class ItemList extends React.Component {
  render() {
    return (
      <ul>
        {this.props.items.map(item => (
          <li key={item.id}>{item.name}</li>
        ))}
      </ul>
    );
  }
}

// Initial list of items
const initialItems = [
  { id: 1, name: 'Apple' },
  { id: 2, name: 'Banana' },
  { id: 3, name: 'Orange' }
];

// Render the component with initial items
ReactDOM.render(<ItemList items={initialItems} />, document.getElementById('root'));

```

Now, let's say we want to update the list of items dynamically:

```js

// Updated list of items
const updatedItems = [
  { id: 1, name: 'Apple' },
  { id: 2, name: 'Banana' },
  { id: 3, name: 'Orange' },
  { id: 4, name: 'Grapes' }, // New item
  { id: 5, name: 'Watermelon' } // New item
];

// Re-render the component with updated items
ReactDOM.render(<ItemList items={updatedItems} />, document.getElementById('root'));

```

Here's what happens behind the scenes:

- React creates a virtual DOM representation of the ItemList component and its contents based on the initial list of items.
- When the list of items changes, React compares the updated virtual DOM with the previous one to identify the differences.
- React then calculates the minimal set of changes needed to update the actual DOM (e.g., adding new items or removing deleted items).
- Finally, React efficiently applies these changes to the actual DOM, resulting in the updated list being displayed on the webpage.



**Shadow DOM**

Shadow DOM allows us to create self-contained components with their own styles and DOM structure, preventing CSS and JavaScript conflicts with the rest of the document.

Simple Code sample for Shadow DOM

```js

// ShadowComponent.js
import React, { useEffect, useRef } from 'react';

const ShadowComponent = () => {
  const shadowHostRef = useRef(null);

  useEffect(() => {
    // Create and attach the shadow root
    const shadowRoot = shadowHostRef.current.attachShadow({ mode: 'open' });

    // Create some content inside the shadow DOM
    const wrapper = document.createElement('div');
    wrapper.setAttribute('class', 'wrapper');

    const info = document.createElement('p');
    info.textContent = 'This is inside the Shadow DOM';

    // Create and apply styles inside the shadow DOM
    const style = document.createElement('style');
    style.textContent = `
      .wrapper {
        background-color: lightgray;
        padding: 10px;
        border-radius: 5px;
      }
      p {
        color: red;
        font-size: 18px;
      }
    `;

    // Append the style and content to the shadow root
    shadowRoot.appendChild(style);
    shadowRoot.appendChild(wrapper);
    wrapper.appendChild(info);
  }, []);

  return (
    <div ref={shadowHostRef} style={{ border: '1px solid black', padding: '10px', margin: '10px' }}>
      Shadow DOM Host
    </div>
  );
};

export default ShadowComponent;

```

<hr>