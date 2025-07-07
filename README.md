
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

### Discord Search Example

in: native before: 2023-03-13

### References

- [Marc's Freya](https://github.com/marc2332/freya)
- [10/4/23 The Future of Blitz](https://github.com/DioxusLabs/dioxus/discussions/1519)
- [Dioxus Labs Projects](https://github.com/orgs/DioxusLabs/projects?query=is%3Aopen)
- [Nical - GUIs on the GPU](https://nical.github.io/drafts/gui-gpu-notes.html)
- [gpu powered markdown viewer](https://github.com/Inlyne-Project/inlyne)
