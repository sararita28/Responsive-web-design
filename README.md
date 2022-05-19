# Responsive Web Design

<em>This repository is meant for note-taking purposes only. If you decide to use it, please do your own due diligence.</em>

### Setting up the emulator
To view the emulator, go to your chrome developer tools. There, you can pick different devices and sizes to see how your content would look on them.

### Introduction
- A responsive website changes depending on the characteristics of the device, meaning that your responsive site needs to apply different styles for different devices.

### Width
- When specifying the width, you should <b>use relative position (such as %) rather than absolute position</b> (such as px). That is because CSS pixels vary 
widely across devices.
- The viewport width on some of the devices can be as low as 320px.

### Tap targets
- <b>Tap targets</b> (i.e. touch, tap, click, input) need to be big and spaced enough and easy to hit. Keep in mind that our fingers are about 10mm wide which is roughly 40CSS pixels, so buttons should be at least 48/48 px. Also, make sure there's at least 40pxs of room between every tap target.

### 
- When you're on a website, in the devtools you can tell whether an element is taking up the entire viewport or not by hovering over it. If you see that the element has
 some orange in it then it is not taking the entire viewport. On the other hand, if it's all blue then it is.

### Applying CSS & Media queries
- There are a few ways to selectively apply CSS. The easiest is with <b>media queries</b>.
 - To add responsive styles, you need to include an additional style sheet in your page, with a media query. For example, if you want your site to react a different way
 when the screen width is at least 500px, you'd add a media attribute and set the value to screen and min-width to 500. example: ``` <link rel="stylesheet" media="screen and (min-width:500px)" href="over500.css">```
 Then in the over500.css file that you've linked you'd add whathever styling you want. You can test it out by increasing your site size in the devtools and seeing the changes.
 - There are 2 other ways you can apply media queries, you can embed them with @media tag, example: ```@media screen and (min-width:500px) { body {color:blue} }```or import them. But avoid importing them at all costs.
 - Linked css vs @media: with linked css, you have many small files, but many http requests. With @add media, you have bigger files but less http requests.
 - The media queries used most often are min-width and max-width. DO NOT use min-device-width and max-device width. Those are based on the device size rather than the browser size.

### Breakpoints
 - Finding the right breakpoints should be done based on the content rather than on specific devices. 
 - To find breakpoints, once you have designed your website for the smallest viewport possible, Open up the devtools and increase the size of your page incrementally. Notice when the content looks like it needs a breakpoint.
- Minor breakpoints: in addition to major breakpoints, you also have minor breakpoints. 
 - Here are the different size classes and breakpoints (not for reference, just to keep in mind because remember: choosing breakpoints should be done based on content)
 <table>
 <tr>
  <th>Breakpoints</th>
  <th>Screen sizes</th>
 </tr>
  <tr>
  <td>Small: up to 640px</td>
   <td>320x569, 360x640, 480x854</td>
 </tr>
 <tr>
    <td>Medium:641px-1007px</td>
   <td>960x540</td>
 </tr>
 <tr>
    <td>Large:over 1008px</td>
   <td>1024x640, 1366x768, 1920x1080</td>
 </tr>
</table>

### Grids & Flexbox
- With the grid fluid system, columns end up wrapping to the next line as the browser width starts getting smaller.
- Flexbox is one of the most powerful tools that you can use for layout because of its ability to fill the space available (If an element has extra room around it it'll expand to fit, else it'll shrink). The default flex direction is row. By default, flex items fit in a single line. To change that add flex-wrap: wrap, which tells the browser that it's ok fot the elements to wrap to the next line. Another useful feature of flexbox is the ability to change the order of elements using the css <em>order</em> attribute.

### Responsive patterns
- There are a couple of responsive patterns that work well across pretty much any device: mostly fluid, layout shifter, column drop, off canvas.
<img src="responsive patterns.png" />
<ul>
 <li>Column drop: at its narrowest viewport, each element simply stacks vertically. As screen gets wider, elements expand until the first breakpoint is hit. At the first breakpoint, 2 elements are now side by side and the 3rd is underneath. For the 3rd breakpoint, things reflow to a 3-column layout. Generally, once the columns hit a max size, instead of getting wider, margins are added to the left and right.</li>
 <li>Mostly fluid: tends to be a bit more grid-like than the column drop. At its narrowest viewport, the elements are stacks. As the layout gets wider, the grid pattern start to appear. When the layout hits its widest viewport, margins are added on the left and right.</li>
 <li>Off-canvas: The off-canvas places less frequently used content off screen, only showing them if the screen is large enough (like meny items for example). See more of this <a href="Responsive-patterns/Off-canvas.md">here</a></li>
</ul>

### Images
- Using the same <b>image</b> but using different resolutions depending on screen size is one of the most common way to make images responsive. The best way to do that is by using the source set attribute on an image tag. However, if your aim is to have a different crop of an image, you should use picture element. Picture element uses media queries to select which image to use.

### Tables
- To prevent <b>tables</b> from overflowing here are 3 of several options: hidden columns, 'no more table' technique, contained tables. 
<ul>
<li>With hidden columns, you only show the important stuff when the screen is small and display everything when the screen allows it not to overflow. The problem with that is that you are hiding content.</li>
 <li>With the 'no more table' technique, below a certain viewport, the table is collapsed(it resembles more a long list as opposed to a table). The nice thing about this is that you can view all your content. To do this, you add a media query on all your elements to display as a block, you get rid of the tr (do that by positioning the content way off screen instead of having a display of none). You also want to add left padding to the td and set its position to relative. Finally, add a position absolution, left:6px, content:attr(data-th) to td:before</li>
</ul>
- An alternative to the previous point, to contain the table in the viewport is to wrap it in a div, set the width to 100%, and overflow-x to auto (this will simply add scrolling to your table.

### Fonts
- <b>Fonts:</b> There's been a consensus about the ideal measure (i.e. length of a line of text) which is 65 chars per line. We need to take into account how people read when designing our app so it is a good idea to use measures as a factor when determining breakpoints. You must also make sure that fonts are big enough to read (at least 16px and a 1.2em line-height).

### Best practices
- By adding the meta 'viewport' tag to the head element of the page, we tell the browser that we know what we're doing. We need to use the meta viewport 
value width = 'device-width' which instructs the page to match the screen's width. 
``` <meta name="viewport" content="width=device-width, initial-scale=1.0"> ```
- Adding the attribute initial-scale = 1 instructs the browser to establish a one-to-one relationship between device-independent pixels & CSS pixels.
- Remember that CSS allows content to overflow its container. To prevent this you can add: max-width='100%'
- <b>Design for the smallest viewport first</b> so you can think of performance from the beginning. It is better to start small (and prioritize content) rather than starting big and then designing down (which might cause you to cur/hide content).
 - You must think about the user experience for every device. 

### Definitions
- Font-boosting : Browser takes the primary content on the page and scales it up for bigger screens.
- Media queries provide easy logic for applying different styles based on device characteristics.
- Breakpoint : the point at which the page changes layout.
- Complext media queries test multiple characteristics rather than just 1.
- <b>There is 1 CSS pixel per 2 hardware pixels.</b>
