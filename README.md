# FlipDiv

A space effecient 3D menu with CSS transitions. FlipDiv works best in browsers with support for CSS 3D transforms, although it falls back on 2D animation for older browsers. It also supports touch events for mobile devices.

[Demo page](http://kireerik.github.io/FlipDiv/demo/) | [Original demo page for Meny](http://lab.hakim.se/meny/)


## Instructions

### 1. Download
Add [FlipDiv.js](https://github.com/kireerik/FlipDiv/blob/master/dist/FlipDiv.js) to your project. The FlipDiv.js file is the only thing required, but you could optionally clone the repository if you want to get the default styles.

Alternatively you can load the FlipDiv.js file from cdnjs, see <https://cdnjs.com/libraries/FlipDiv>.

### 2. Markup
FlipDiv requires two HTML elements to work: a **menu** and the page **contents**. The class names are not used by the library so chose anything you want.

```html
<body>
  <div class="flipDiv">
    <!-- your menu items -->
  </div>
  <div class="contents">
    <!-- your page contents -->
  </div>
</body>
```

Some rules, notes and best practices to keep in mind in terms of markup and styling:
- The **menu** and **contents** should have the same **parent** element.
- The background which appears behind the **contents** when FlipDiv is open is not added by the library. You need to set your desired background to the **parent** element. The default style can be found in [index.css](https://github.com/kireerik/FlipDiv/blob/master/demo/index.css#L24).
- The arrow which appears when FlipDiv is closed is also not added by the library, if you want it you can easily copy the styles from the demo.css.
- The **menu** container will be automatically resized by the library according to configuration options.
- FlipDiv works on scrolling pages as the menu itself is fixed.


### 3. Initialize
Next you need create an instance of FlipDiv and tell it which HTML elements to use. This should be done after the **FlipDiv.min.js** is included on your page. Example using the HTML below:

```javascript
var flipDivMenu = FlipDiv.create({
	// The element that will be animated in from off screen
	menuElement: document.querySelector( '.flipDiv' )

	// The contents that gets pushed aside while FlipDiv is active
	, contentsElement: document.querySelector( '.contents' )

	// The alignment of the menu (top/right/bottom/left)
	, position: 'left'

	// The height of the menu (when using top/bottom position)
	, height: 200

	// The width of the menu (when using left/right position)
	, width: 260

	// The angle at which the contents will rotate to.
	, angle: 30

	// The mouse distance from menu position which can trigger menu to open.
	, threshold: 40

	// Width(in px) of the thin line you see on screen when menu is in closed position.
	, overlap: 6

	// The total time taken by menu animation.
	, transitionDuration: '0.5s'

	// Transition style for menu animations
	, transitionEasing: 'ease'

	// Gradient overlay for the contents
	, gradient: 'rgba(0,0,0,0.20) 0%, rgba(0,0,0,0.65) 100%)'

	// Use mouse movement to automatically open/close
	, mouse: true

	// Use touch swipe events to open/close
	, touch: true
})
```

### 4. API & Events
A few handy methods API methods are included, you call these on the instance returned by ```FlipDiv.create``` (see above).

```javascript
flipDivMenu.configure({ mouse: false }); // change settings after initialization

flipDivMenu.open()

flipDivMenu.close()

flipDivMenu.isOpen() // true/false

flipDivMenu.destroy() // revert original DOM state, unbind events
```

The wrapper element (parent of the **menu** and **contents**) is decorated with classes based on its state:
```css
.flipDiv-active
.flipDiv-top
.flipDiv-right
.flipDiv-bottom
.flipDiv-left
```

Instances of FlipDiv dispatch events to notify you of their state:

```javascript
var flipDivMenu = FlipDiv.create( ... ) // see 3. Initialize

flipDivMenu.addEventListener('open', function() {

	// do something on open

})

flipDivMenu.addEventListener('close', function() {

	// do something on close

})

flipDivMenu.addEventListener('opened', function() {

	// do something right after FlipDiv is opened and transitions finished

})

flipDivMenu.addEventListener('closed', function() {

	// do something right after FlipDiv is closed and transitions finished

})
```

## Credits
Special thanks to the original author Hakim El Hattab (@hakimel) and those who are contributed to the original project called [Meny](https://github.com/hakimel/Meny)!


## History

[Releases](https://github.com/kireerik/FlipDiv/releases)

[Previous releases for Meny](https://github.com/hakimel/Meny#history)

## License

MIT licensed

Copyright (C) 2015 Erik Engi, 2014 Hakim El Hattab, http://hakim.se