# Lifecycle Methods

In ReactJS, components go through various stages in their lifecycle, from initialization to destruction.

**Mounting Phase:** 

- constructor(): This is the first method called when a component is created. It is used for initializing state and binding event handlers.

- render(): This method is required and must return JSX representing the component's UI. It is called each time the component needs to re-render.

- componentDidMount(): This method is called after the component is rendered for the first time. It is commonly used for performing side effects such as data fetching or setting up event listeners.


**Updating Phase:**

- render(): Again, the render() method is called whenever the component needs to re-render due to changes in state or props.

- componentDidUpdate(prevProps, prevState): This method is called after a component's update is flushed to the DOM. It is used for performing side effects in response to props or state changes.

- shouldComponentUpdate(nextProps, nextState): This method is called before rendering when new props or state are received. It allows developers to control whether the component should re-render or not based on the new values.


**Unmounting Phase:**

- componentWillUnmount(): This method is called just before the component is removed from the DOM. It is used for cleanup tasks such as removing event listeners or canceling subscriptions.


**Error Handling:**

- componentDidCatch(error, info): This method is called when an error occurs during rendering, in lifecycle methods, or in the constructor of any child component. It is used to catch and handle errors within the component tree.

<hr>