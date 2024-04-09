# Event bubbling, capturing and Delegation


**Event bubbling:** When clicking the button with id "child" will trigger both the event listener on the button itself and the event listener on its parent div.

```js

<div id="parent">
    <button id="child">Click Me</button>
</div>

<script>
    document.getElementById('parent').addEventListener('click', function() {
        console.log('Parent element clicked');
    });

    document.getElementById('child').addEventListener('click', function(event) {
        console.log('Child element clicked');
        event.stopPropagation(); // Stop event from bubbling up
    });
</script>

```

**Event capturing:** When clicking the button with id "child" will trigger the event listener on its parent div first due to event capturing (true as the third argument in addEventListener()). Then, the event will propagate down to the button itself.

```js

<div id="parent">
    <button id="child">Click Me</button>
</div>

<script>
    document.getElementById('parent').addEventListener('click', function() {
        console.log('Parent element clicked');
    }, true); // true for event capturing

    document.getElementById('child').addEventListener('click', function() {
        console.log('Child element clicked');
    });
</script>

```

**Event Delegation:** Let's suppose, We have a list (ul) with multiple list items (li). Instead of attaching event listeners to each individual list item, we attach a single event listener to the parent ul element. When a list item is clicked, the event bubbles up to the ul, and we can determine which list item was clicked by checking the event.target. 

```js

<ul id="parent">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>

<script>
    document.getElementById('parent').addEventListener('click', function(event) {
        if (event.target.tagName === 'LI') {
            console.log('Clicked on list item: ' + event.target.textContent);
        }
    });
</script>

```

<hr>
