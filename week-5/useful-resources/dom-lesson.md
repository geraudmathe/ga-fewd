The DOM and the Web Browser
===========================

## JavaScript vs the DOM

The **Document Object Model**, or DOM, is the interface that allows you to programmatically access and manipulate the contents of a web page (document). It provides a structured, object-oriented representation of the individual elements and content in a webpage with methods for **getting** and **setting** the properties of those objects.

It also provides methods for **adding** and **removing** such objects, allowing you to create dynamic content on the client-side rather than the server-side without reloading the page! Exciting!

The DOM also provides an interface for dealing with events, **allowing you to capture and respond to user or browser actions**.
t.


## Javascript vs the browser

Javascript is not the same as the web browser. And the web browser is not the same as JavaScript. You can run your Javascript code without a web browser. But it is a pain.

Generally, we want to write javascript that runs in the browser, (we use Chrome).

### In short:

The DOM lets us do two things:

- Manipulate the document, add, remove, retrieve, edit/update etc...
- Run code when things happen.

## Event driven programming

We've written a couple of different kinds of programs so far. Imperative ones, and Object-Oriented ones.

- **Imperative** code that starts at the top line, and chugs down through it until it finishes.
- **Object oriented** programs, where we define a bunch of objects and then our code jumps around as necessary.

But we've also written **event-driven** programs, though we haven't called them that.

- When our web server runs, it sets up our app and then just sits there.
- It's not until something happens - an event - our visit to the web page - that our code runs.

We can define events on elements, and what JS to run when those events happen.

## addEventListener

The javascript `addEventListener()` method attaches an event handler to a specified element). Usually we select that element using an id.

```
element.addEventListener(event, function, useCapture);
```

- `element` in this case is the DOM object that you want listener to operate on (you have to get it first)
- The first parameter is the `type of the event` (like "click" or "mousedown").
- The second parameter is then name of the `function we want to call` when the event occurs.
- The third parameter is a boolean value specifying whether to use `event bubbling` or `event capturing`.

This parameter is optional, (we'll go into more detail later).

## Click events / Mouse events

"Open In Browser" the first file: `click_events.html`

Javascript allows us to capture and use click events.
Open the Javascript Console in Chrome and let's open the javascript console (cmd + alt + j).

```
More Tools > Developer Tools > Javascript Console
```

You can bind an onclick event inline (directly on an element), like this:

```
<button onclick="alert('Hello WDI!');">I'm a button!</button>
```

However, this inline javascript considered "bad practise". It's better to get the element using javascript:

```
var element = document.getElementById("event_click")
```

Looking for onclick events is a very common event in web browsers. Let's look at 4 kinds of onclick events:

- "click"

```
element.addEventListener("click", function(e) {
  alert("I've been clicked!");
});
```

- "dblclick"

```
element.addEventListener("dblclick", function(e) {
  alert("I've been clicked!");
});
```

- "mousedown"

```
element.addEventListener("mousedown", function(e) {
  alert("I've been clicked!");
});
```

- "mouseup"

```
element.addEventListener("mouseup", function(e) {
  alert("I've been clicked!");
});
```

## Key events
Open the next file: `key_events.html`.
This time we'll log the responses to the console.

- "keypress"

```
document.getElementById("key_event").onkeypress = function(e) {
   console.log("keypressed!");
};
```

The addEventListener() method is not supported in Internet Explorer 8 and earlier versions. This is another method of creating en eventListener.

We can split keypress into two parts:

- "keydown"

```
element.addEventListener("keydown", function(e) {
   console.log("keydown!");
});
```

- "keyup"

```
element.addEventListener("keyup", function(e) {
   console.log("keyup!");
});
```

## Hover events
Open the next file: `hover_events.html`

Take a look at the code for the image of Bill Murray (it's got some basic styling):

```
<img id="bill" src="http://fillmurray.com/200/301" />
```

And the corresponding javascript:

```
var bill = document.getElementById("bill");

bill.onmouseover = function(e) {
  console.log("mouseover #bill");
  this.setAttribute('src', 'http://fillmurray.com/200/300');
}

bill.onmouseout = function(e) {
  console.log("mouseout #bill");
  this.setAttribute('src', 'http://fillmurray.com/200/301');
}
```

In the context of the event, `this` means the element that the event is operating on (so the image tag in this example). And any document element can have events bound to it, and we can always use the console to see what's going on.

Aside - try:

```
<body onlick="console.log(this)">
```

For a slightly more complicated example, let's have a look at:

- "mousemove"

```
document.getElementById("mouseHover").addEventListener("mouseover", function(e) {
  this.addEventListener("mousemove", function(e) {
    console.log(e.pageX, e.pageY, (e.pageY/500))
    this.style.opacity = (e.pageY/500);
    this.style.filter  = 'alpha(opacity=' + (e.pageY/500) + ')';
  });
});

document.getElementById("mouseHover").addEventListener("mouseout", function(e) {
  console.log("you've left the element");
});
```

In this code we are creating a listener for `this` which will log the X & Y coordinates of our mouse and change the `style` property of the element.

## Form events
Open the next file: `form_events.html`

Like click events, forms are very common things to have to deal with on a website.

- "focus"

```
element.addEventListener("focus", function(e) {
   console.log("focus!");
});
```

- "blur"

```
element.addEventListener("blur", function(e) {
   console.log("blur!");
});
```

- "change"

```
var radios = document.getElementsByClassName("radio_event")

for( var i=0; i<radios.length; i++ ) {
  radios[i].addEventListener("change", function(e) {

    for( var a=0; a<radios.length; a++ ) {
      radios[a].checked=false;
      console.log(radios[a]);
    }

    this.checked=true;
    console.log('Radio selected');
  });
}
```

- "submit"

```
document.getElementById('form_event').addEventListener("submit", function(e) {
   alert("Form submitted");
   console.log("Form submitted");
   return false;
});
```

## Window events
Open the next file: `window_events.html`

As well as interacting with elements inside the page, like clicking items or interacting with forms. You can also access information when you change the browser window.

- Window "resize" event

```
window.onresize
```

- Window "scroll" event

```
window.onscroll
```

## Event Bubbling - Lowest to highest
Open the next file: `bubbling_events.html`

The concept of **event bubbling** was introduced to deal with situations where a single event, such as a mouse click, may be handled by two or more event handlers defined at different levels of the **Document Object Model (DOM)** hierarchy. If this is the case, the event bubbling process starts by executing the event handler defined for individual elements at the **lowest level** (e.g. individual hyperlinks, buttons, table cells etc.). From there, the event bubbles up to the containing elements (e.g. a table or a form with its own event handler), then up to even higher-level elements (e.g. the BODY element of the page). Finally, the event ends up being handled at the highest level in the DOM hierarchy, the document element itself (provided that your document has its own event handler).

## Event Capturing - Lowest to highest
Event capturing is the opposite of bubbling (events are handled at higher levels first, then sink down to individual elements at lower levels). Event capturing is supported in fewer browsers and rarely used; notably, Internet Explorer prior to version 9.0 does not support event capturing.

### Event Propagation

The term **event propagation** is often used as a synonym of event bubbling. However, strictly speaking, event propagation is a wider term: it includes not only **event bubbling** but also **event capturing**.

```
.stopPropagation();
```


-----------------------------

### Inheritance

- With some languages, like Ruby, we say they have *classical inheritance*. It's not about being *classic*; it's about being *class*-based. We create objects, which are **instances of a class**.
- JavaScript doesn't have Classical inheritance. It has *prototypal inheritance*. Our objects inherit directly from other objects.

### Resources

- MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference?redirectlocale=en-US&redirectslug=JavaScript%2FReference
- JavaScript puzzlers: http://javascript-puzzlers.herokuapp.com
