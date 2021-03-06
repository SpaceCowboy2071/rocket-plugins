# Rocket Reveal for jQuery
Reveals elements based on the vertical scroll position of the browser.


## Documentation
### Usage
Call the plugin on the containing element of the elements to be revealed as the page is scrolled.  All elements that are managed by the reveal manager need to have the class `rkt-reveal`.  When each element has passed the verical threshold, the `rkt-reveal-in` class will be added.

```javascript
$( "#my-container" ).rktReveal();
```

Or alternatively to override the default options:

```javascript
$( "#my-container" ).rktReveal( {
	stagger: 0.2,
	threshold: 0.7
} );
```


### Styles
The reveal plugin can work with either CSS animations or transitions.  Any transforms on the elements will be factored out when calculating the element's offset top position.

```css
.rkt-reveal {
	opacity: 0;
	transform: translateY( 100% );
	transition-property: opacity, transform;
	transition-duration: 1s;
}

.rkt-reveal.rkt-reveal-in {
	opacity: 1;
	transform: translateY( 0% );
}

```


### Options
Options can be passed via JavaScript within an object or as data attributes.  Options set in JavaScript will take precedence over data attributes.  For data attributes, append the option name to `data-`, as in `data-interval=""` in the DOM.

**stagger** (Number) When several elements pass the threshold at once, the animation/transition in is staggered.  This time is represented in seconds.  Default `0.1`.

**threshold** (Number) The percentage ratio based off of the window height that an element's top position must pass before it is revealed.  Default `0.9`.



### Methods
You can call additional methods on a reveal managed element by calling the plugin on the element and using one of the following commands as a string parameter (e.g. `$( "#my-container" ).rktReveal( "update" );`).

**destroy()** (Void) Destroys the reveal manager for all matching elements.

**disable()** (Void) Disables the resize and scroll event listeners.

**enable()** (Void) Enables the resize and scroll event listeners.

**refresh()** (Void) Searches the containing element for additional elements that have the `rkt-reveal` class.  Useful if elements are dynamically added after the plugin has been initialized.  *(NOTE: This method automatically calls the update method)*

**update()** (Void) Forces the manager to check if any element has passed the threshold.  Useful if the DOM has changed but not triggered an resize or scroll event, such as window load.



## Examples
(TBD)


## History
### v0.0.7
Fixed an issue where elements/items that weren't starting from a transformed style would return an error when retrieving the offset.

### v0.0.5
Added detection and utilization of passive event listeners for scrolling.

### v0.0.4
Added ability to set options via JavaScript.

### v0.0.3
Added event handling for animation/transition end, in which the reveal classes are removed.  This will allow the browser to display the items without using the GPU if desired.

### v0.0.2
Added custom debouncing and throlling of resize and scroll events.  Added fix so that transitions can be used instead of animations.

### v0.0.1
Added to GitHub after using in several projects.
