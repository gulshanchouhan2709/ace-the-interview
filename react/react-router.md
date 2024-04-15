# React Router

React Router is a popular library for handling routing in React applications. It allows developers to define different routes for different parts of the application and renders the appropriate components based on the current URL.

**BrowserRouter or HashRouter:**

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

<hr>