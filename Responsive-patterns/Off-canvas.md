Say you have a website with a navigation menu. In a narrow viewport, you  this navigation menu is hidden until the hamburger menu is clicked.
In other cases, the hidden content comes in from off the screen. The code for this example would look something like this:
You have 2 elements :
The navigation menu and the main content:
```
<nav id="drawer" />
<main />
```
Make sure the elements take up the full viewport width:
```
html, body, main {
width: 100%;
}
```
The styles for the off-canvas nav element:
```
nav {
  width:300px; //be careful to keep it reasonably sized as to not overflow
  height:100%;
  position:absolute;
  transform: translate(-300px,0); //use this to move it off the screen
  transition: transform 0.3s ease; //nice animation
}

nav.open { 
  transform: translate(0,0);
}
```
Breakpoint (at 600px for example) to reposition everything back to its normal spot:
```
@media screen and (min-width:600px) {
  nav {
    position: relative;
    transform: translate(0,0) //resets the transform
  }
  body {
    display: flex;
    flex-flow: row nowrap;
  }
  main {
    width: auto;
    flex-grow: 1; // allows elements to take the full remaining width of the viewport
  }
}
```
Finally, add
```
menu.addEventListener('click', function(e) {
  drawer.classList.toggle('open')
  e.stopPropagation()
})
```
