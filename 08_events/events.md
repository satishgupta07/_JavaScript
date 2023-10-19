# Introduction to events

```Javasciprt
    const btn = document.querySelector("button");

    function random(number) {
    return Math.floor(Math.random() * (number + 1));
    }

    btn.addEventListener("click", () => {
    const rndCol = `rgb(${random(255)}, ${random(255)}, ${random(255)})`;
    document.body.style.backgroundColor = rndCol;
    });
```

## Event: type property
```Javasciprt
    // Keyboard events
    document.addEventListener("keydown", getEventType, false); // first
    document.addEventListener("keypress", getEventType, false); // second
    document.addEventListener("keyup", getEventType, false); // third

    // Mouse events
    document.addEventListener("mousedown", getEventType, false); // first
    document.addEventListener("mouseup", getEventType, false); // second
    document.addEventListener("click", getEventType, false); // third
```

## Event: timeStamp property
The timeStamp read-only property of the Event interface returns the time (in milliseconds) at which the event was created.

```Javasciprt
    function getTime(event) {
        const time = document.getElementById("time");
        time.firstChild.nodeValue = event.timeStamp;
    }
    document.body.addEventListener("keypress", getTime);
```

## Event: target property
The read-only target property of the Event interface is a reference to the object onto which the event was dispatched.

```Javasciprt
    function hide(evt) {
        // evt.target refers to the clicked <li> element
        // This is different than evt.currentTarget, which would refer to the parent <ul> in this context
        evt.target.style.visibility = "hidden";
    }

    // Attach the listener to the list
    // It will fire when each <li> is clicked
    ul.addEventListener("click", hide, false);
```

## Event: defaultPrevented property
```Javascript
    function stopLink(event) {
    event.preventDefault();
    }
```


***********************************************************

# JavaScript Events: Bubbling, Capturing, and Propagation

## What is “propagation”?
Propagation refers to how events travel through the Document Object Model (DOM) tree.

## Event Bubbling and Capturing
Bubbling and Capturing are the two phases of propagation. In their simplest definitions, bubbling travels from the target to the root, and capturing travels from the root to the target.