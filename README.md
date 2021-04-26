# EZ Block Diagram
Embeddable, Zoomable Block Diagram

This is a organization tool idea that has been floating around in my head for awhile. Basically, I have all these projects with structures that I want to communicate in an easy to understand block diagram. I have been doing this for years now with Gravit Designer (huge shout out: [designer.io](https://designer.io) which looks great but can take a few minutes to produce and it generates an image which must be re-generated and replaced with every change. My goal is to create a simple json file that can quickly be edited to create a block diagram with the added benefits of being able to zoom in (a la Prezi) and be able to easily embed it into a web page.

Obvious choice here is to use `javascript` (web dev, built-in json compatability, dynamicly positioned elements, easily embedable, static web content) and the `canvas` element seemed like a good starting point. A pinch of w3 schools and now I am well on my way...

### Goals
- [x] embeddable (simple to insert into an web page/HTML context)
- [ ] zoomable (click to zoom in on an element and further visualize contents)
- [x] inline json/json file (just write a plain text json file to produce diagram, super easy to change)
- [x] percentage based (dimensions are percentage based and relative to their parent element so you don't have to think much when creating a diagram)
- [ ] element support (supports all elements typically used in block diagrams)
    - [x] rectangles
    - [x] lines
    - [x] text/labels (text if you want to position text somewhere, label if you just want text right in the middle)
    - [ ] images

