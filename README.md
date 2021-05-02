# EZ Block Diagram
Embeddable, Zoomable Block Diagram

This is a organization tool idea that has been floating around in my head for awhile. Basically, I have all these projects with structures that I want to communicate in an easy to understand block diagram. I have been doing this for years now with Gravit Designer (huge shout out: [designer.io](https://designer.io) which looks great but can take a few minutes to produce and it generates an image which must be re-generated and replaced with every change. My goal is to create a simple json file that can quickly be edited to create a block diagram with the added benefits of being able to zoom in (a la Prezi) and be able to easily embed it into a web page.

Obvious choice here is to use `javascript` (web dev, built-in json compatability, dynamicly positioned elements, easily embedable, static web content) and the `canvas` element seemed like a good starting point. A pinch of w3 schools and now I am well on my way...

### Builds
- `1.0` basic rectangles using `javascript canvas`
- `1.1` labels/lines/text added to `canvas`
- `2.0` switch from `canvas` to `svg` with `1.1` levels of functionality

### Goals
- [x] embeddable (simple to insert into an web page/HTML context)
- [ ] zoomable (click to zoom in on an element and further visualize contents)
- [x] inline json/json file (just write a plain text json file to produce diagram, super easy to change)
- [x] percentage based (dimensions are percentage based and relative to their parent element so you don't have to think much when creating a diagram)
    - [ ] optional padding to keep percentage math simple
- [ ] element support (supports all elements typically used in block diagrams)
    - [x] rectangles
    - [x] lines
    - [ ] circles
    - [x] text/labels (text if you want to position text somewhere, label if you just want text right in the middle)
    - [ ] images
- [ ] default values (stroke widths, colors, 
- [ ] easy svg/png download

### Menu Buttons
- [ ] Download SVG
- [ ] Download PNG
- [ ] Zoom Home

### Early Demonstration (Version 2.0)
The following `json` will generate the `svg` below on your page

```javascript
var data = {
    car: {
        type: "rect",
        color: "blue",
        per: [0, 0, 100, 100],
        carTitle: {
            type: "text",
            color: "white",
            per: [50, 5],
            text: "Cars"
        },
        sportsCar: {
            type: "rect",
            color: "red",
            per: [5, 10, 95, 95],
            sportsCarTitle: {
                type: "text",
                color: "white",
                per: [50, 5],
                text: "Sports Cars"
            },
            mustang: {
                label: "Mustang",
                type: "rect",
                color: "silver",
                per: [5, 10, 45, 95],
                mach1: {
                    label: "Mach 1",
                    type: "rect",
                    color: "black",
                    per: [20, 60, 80, 75],
                },
                boss429: {
                    label: "Boss 429",
                    type: "rect",
                    color: "purple",
                    per: [20, 75, 80, 90],
                }
            },
            camaro: {
                label: "Camaro",
                type: "rect",
                color: "orange",
                per: [55, 10, 95, 95],
            },
            mustangCamaro: {
                label: "Link",
                type: "line",
                color: "navy",
                per: [45, 52, 55, 52],
                width: 10
            }
        }
    }
}
```

![Demo 2.0](/demo-2.0.jpg)

```html
<svg id="ezbd" width="1200px" height="720px">
    <rect fill="blue" x="0" y="0" width="1200" height="720" rx="20"></rect>
    <text fill="white" alignment-baseline="central" text-anchor="middle" font-size="40px" x="600" y="36">Cars</text>
    <rect fill="red" x="60" y="72" width="1080" height="612" rx="20"></rect>
    <text fill="white" alignment-baseline="central" text-anchor="middle" font-size="40px" x="600" y="102.6">Sports Cars</text>
    <rect fill="silver" x="114" y="133.2" width="432" height="520.1999999999999" rx="20"></rect>
    <text fill="white" alignment-baseline="central" text-anchor="middle" font-size="40px" x="330" y="393.29999999999995">Mustang</text>
    <rect fill="black" x="200.4" y="445.32" width="259.2" height="78.03" rx="20"></rect>
    <text fill="white" alignment-baseline="central" text-anchor="middle" font-size="40px" x="330" y="484.335">Mach 1</text>
    <rect fill="purple" x="200.4" y="523.35" width="259.2" height="78.03" rx="20"></rect>
    <text fill="white" alignment-baseline="central" text-anchor="middle" font-size="40px" x="330" y="562.365">Boss 429</text>
    <rect fill="orange" x="654" y="133.2" width="432" height="520.1999999999999" rx="20"></rect>
    <text fill="white" alignment-baseline="central" text-anchor="middle" font-size="40px" x="870" y="393.29999999999995">Camaro</text>
    <line x1="546" y1="390.24" x2="654" y2="390.24" stroke="navy" stroke-width="4px"></line>
    <text fill="white" alignment-baseline="central" text-anchor="middle" font-size="40px" x="600" y="390.24">Link</text>
</svg>
```

