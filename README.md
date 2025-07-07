
### Blitz Native Discord Channel Notes

- [9/9/2022](https://discord.com/channels/899851952891002890/954257659597553664/1017780518449852417)
- [1/3/2023 Nico Burns](https://discord.com/channels/899851952891002890/954257659597553664/1059881306487521310)
- [2/14/2023 Discussing ECS Model](https://discord.com/channels/899851952891002890/954257659597553664/1075190512669175828)

---

The code that is related to the Tao window curretly would need to be converted into something more like a viewport. It wouldn't be the window that the bevy app runs in, just something with a size inside of that window that the Blitz UI is rendered into that can capture events
You don't need direct access, but there needs to be a size so that layout can work, and events so that elements can respond to actions

It would happen at the Blitz level. Native core is just an abstraction for an incrementally computed tree of styles/attributes. It doesn't know how to render or what a window is

Layout needs to depend on the font size of the current node and the layout of children which was not possible in the old incremental tree system, but should be possible now

- [3/14/23](https://discord.com/channels/899851952891002890/954257659597553664/1085265677209833512)

---

How difficult would it be to associate/store extra non-style attributes with a node in Blitz?  (/how would one go about doing this). The use case I'm thinking of is image nodes which ought to have a their native width/height/aspect-ratio stored seperately from the style versions of those properties (so that if for example a user sets just the width, then the height can be automatically computed from it's native aspect ratio). Ideally each type of node (text, image, div, etc) should have a different set of attributes associated with it.

- [4/11/23](https://discord.com/channels/899851952891002890/954257659597553664/1095302598682234910)

---

*There is a very nice picture of the rendered frames in time*

It seems like batching would be something that needs to integrate with Vello or be built into Vello, not Blitz.  Invalidation would cut out almost all of the work in that scene. When you hover over a button in that scene we only need to redraw that one box, but we redraw all 10k boxes instead. Native core outputs information about what parts of the computed styles have changed, we just need to take that output and only rerender the elements that changed

- [4/20/23](https://discord.com/channels/899851952891002890/954257659597553664/1098675935974273034)

---

Im wondering what drives the decision to use wgpu for native (and have to implement UI from scratch) for “native” instead of creating/use bindings for swift and android. Both shit ton of work of course but just wondering

- [9/1/23](https://discord.com/channels/899851952891002890/954257659597553664/1147236487180599346)

---

Office applications are another example of something I wouldn't really want to build on top of the web platform. Neither a word processor (because I want to do custom text layout and rendering), nor a spreadsheet (because I want do infinite cells and virtualised rendering and the web is crap at this).
I think basically anything that is a "serious" desktop app:

- Office Suite
- CAD Software
- Figma
- Adobe Suite
- etc.

You might say that those apps are going web. But the web versions don't tend to be good. And I think a lot of the reason they're going web is because it's miles ahead of anything else for cross-platform development.

If that could be changed then we might see a revival of the native app
Possibly Dioxus is not the project to do that, but I think it's a goal worth striving for

##### matthunz — 10/18/23, 2:09 PM

*Totally agree! I think dioxus is currently the best rust UI state management tool out there so it should be a great fit for native.*

@marc 's Freya looks great and I wonder if that should become the official native platform. Blitz is a cool idea but I can see why it's getting depreciated: it'll be years before we could make a new web browser. That's why I'd love to see a direction to native components that we can incrementally grow over time
Another idea I had was using xilem's widget tree as a backend but that's also taking a long time
Something else I've noticed is dioxus-desktop might be fairly limited. Animations and such over RPC will probably be much slower than with native


- [10/18/23](https://discord.com/channels/899851952891002890/954257659597553664/1164306527314772079)

---

Lots of information on November 10, 2023

- [11/11/23](https://discord.com/channels/899851952891002890/954257659597553664/1172872457418440704)

---

As I said in the Future of Blitz issue on GH, I would be a little scared if you went to something non-html as I think that is one of the  key differences with freya. But anyway, It's up to you.

I can think of:

- Xilem is building their own with vello
- Floem is using vger
- Vizia is using femtovg
- Iced has a tiny-skia renderer, but also a wgpu one.
- Freya is using actual skia

I think it would be cool to make something where a single end-user API can be "lowered" to both the native renderer and an actual web browser

Kinda React Native style but with better web support

I guess not really react-native style on the native side because it wouldn't be platform-specific renderers. But the idea that a single UI definition can be lowered to multiple backends is react-native-ish

React-native does this well. It allows you to provide modules backed by native Android/iOS code that can be used by cross-platform apps.

Some built-in RN components also have properties than only work on some platforms (and you can detect which platform you're on at the JS level and do slightly different things if you want to)

Yes for example, a Box component that when targeting freya turns into a rect and when targeting web turns into a div

Yes, exactly. Something like Box all gets easier if you just support web-style layout though (or at least a decent common subset). Because you don't really want to be writing your UI layouts twice.

The trait abstracts over common capabilities that UI elements need to be able to do like:

- Layout (compute size and position)
- Paint (draw to screen)
- Accessibility (expose an accessibility tree to the os)
- Event handling (respond to input and pass messages up and down the tree)

---

- [11/16/23](https://discord.com/channels/899851952891002890/954257659597553664/1174711715833839647)

---

- [Stylo Dioxus In the Beginning](https://github.com/jkelleyrtp/stylo-dioxus)
- [1/16/24](https://discord.com/channels/899851952891002890/954257659597553664/1196853533404840016)

---

### What is Canvas

What is Canvas (in web development)?

In web development, a canvas is an HTML element that acts as a container for graphics, allowing you to draw and manipulate images, shapes, and other visual content programmatically using JavaScript. Think of it as a blank drawing board where you control every pixel. It's especially useful for things like:
Games: Fast rendering of 2D graphics.

Data Visualization: Creating dynamic charts, graphs, and interactive visualizations.
Animations: Drawing and updating graphics quickly to create smooth animations.
Image Editing: Manipulating and processing images directly within the browser.

Canvas vs. DOM Rendering

The Document Object Model (DOM) is a structured representation of the content of a web page, where each element is a separate object that can be manipulated. Canvas, on the other hand, is a pixel-based approach where everything you draw becomes part of a single image.

Seeking a Single API:

While the DOM and Canvas serve distinct purposes and have different rendering models, you're asking about a single API to render to both DOM (nodes, not canvas) and Canvas. This is a challenging request because of their fundamental differences:

DOM: Retained mode rendering, where the browser keeps track of elements and their properties, allowing for easy manipulation, accessibility, and integration with CSS.

Canvas: Immediate mode rendering, where you directly control pixels, leading to high performance for graphics and animations but requiring more manual management of elements and events.


### Discord Search Example

in: native before: 2023-03-13

### References

- [css layout explained](https://dev.to/adrianbdesigns/css-houdini-s-layout-api-explained-33pa)
- [Marc's Freya](https://github.com/marc2332/freya)
- [10/4/23 The Future of Blitz](https://github.com/DioxusLabs/dioxus/discussions/1519)
- [Dioxus Labs Projects](https://github.com/orgs/DioxusLabs/projects?query=is%3Aopen)
- [Nical - GUIs on the GPU](https://nical.github.io/drafts/gui-gpu-notes.html)
- [gpu powered markdown viewer](https://github.com/Inlyne-Project/inlyne)
