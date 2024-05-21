# Diff & Reconciliation & React Fiber


**Diff algorithm**

The "Diff algorithm" is a process that compares the current virtual DOM with a new virtual DOM to identify changes.


Element Type Comparison: If the elements are of different types (e.g., <div> vs. <span>), React will tear down the old tree and build a new tree from scratch. However, if the elements are of the same type, React will continue to compare their attributes and children.

Keyed Elements: React uses keys to identify elements across renders. Keys help React understand which elements have changed, been added, or removed. This is particularly important for lists of elements.



**Reconciliation Algorithm:**

The "Reconciliation Algorithm" updates the actual DOM based on the differences found by the diff algorithm, ensuring minimal and efficient updates.


Virtual DOM Representation: React creates a lightweight copy of the actual DOM called the virtual DOM. When the state of a component changes, React updates the virtual DOM instead of the actual DOM.

Patching: React calculates the minimal set of changes needed to update the actual DOM based on the differences identified. This could involve updating attributes, adding or removing nodes, or rearranging nodes.


**React Fiber:**

React Fiber is the new core reconciliation algorithm in React that allows for more efficient and flexible rendering. It breaks down rendering work into smaller chunks and prioritizes updates, making the user interface more responsive and smooth, especially during complex or heavy tasks.

<hr>