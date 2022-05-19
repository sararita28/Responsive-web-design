# Responsive Web Design

This repository is meant for note-taking purposes only. If you decide to use it, please do your own due diligence.

### Setting up the emulator
To view the emulator, go to your chrome developer tools. There, you can pick different devices and sizes to see how your content would look on them.

### 
- A responsive website changes depending on the characteristics of the device, meaning that your responsive site needs to apply different styles for different devices.
- 1CSS pixel per 2 hardware pixels
- By adding the meta 'viewport' tag to the head element of the page, we tell the browser that we know what we're doing. We need to use the meta viewport 
value width = 'device-width' which instructs the page to match the screen's width. 
``` <meta name="viewport" content="width=device-width, initial-scale=1.0"> ```
- Adding the attribute initial-scale = 1 instructs the browser to establish a one-to-one relationship between device-independent pixels & CSS pixels.
- <b>When specifying the width</b>, you should use relative position (such as %) rather than absolution position (such as px). That is because CSS pixels vary 
widely across devices.
Remember that CSS allows content to overflow its container. To prevent this you can add: max-width='100%'
- The viewport width on some of the devices can be as low as 320px.
- <b>Tap targets</b> (i.e. touch, tap, click, input) need to be big and spaced enough and easy to hit. Keep in mind that our fingers are about 10mm wide which is 
roughly 40CSS pixels, so buttons should be at least 48/48 px. Also, make sure there's at least 40pxs of room between every tap target.
- <b>Design for the smallest viewport first</b> so you can think of performance from the beginning. It is better to start small (and prioritize content) rather than starting big and then designing down (which might cause you to cur/hide content).
- When you're on a website, in the devtools you can tell whether an element is taking up the entire viewport or not by hovering over it. If you see that the element has
 some orange in it then it is not taking the entire viewport. On the other hand, if it's all blue then it is.
 - You must think about the user experience for every device. 
 - There are a few ways to selectively apply CSS. The easiest is with <b>media queries</b>.
 - To add responsive styles, you need to include an additional style sheet in your page, with a media query. For example, if you want your site to react a different way
 when the screen width is at least 500px, you'd add a media attribute and set the value to screen and min-width to 500. example: ``` <link rel="stylesheet" media="screen and (min-width:500px)" href="over500.css">```
 Then in the over500.css file that you've linked you'd add whathever styling you want. You can test it out by increasing your site size in the devtools and seeing the changes.
 - There are 2 other ways you can apply media queries, you can embed them with @media tag, or import them. But avoid importing them at all costs.
### Definitions
- Font-boosting : Browser takes the primary content on the page and scales it up for bigger screens.
- Media queries provide easy logic for applying different styles based on device characteristics.
