
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

### Ref

in: native before: 2023-03-13
