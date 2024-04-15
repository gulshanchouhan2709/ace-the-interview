# Virtual DOM

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

<hr>