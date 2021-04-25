# EZ Block Diagram
Embeddable, Zoomable Block Diagram

This is a organization tool idea that has been floating around in my head for awhile. Basically, I have all these projects with structures that I want to communicate in an easy to understand block diagram. I have been doing this for years now with Gravit Designer (huge shout out: [designer.io](https://designer.io) which looks great but can take a few minutes to produce and it generates an image which must be re-generated and replaced with every change. My goal is to create a simple json file that can quickly be edited to create a block diagram with the added benefits of being able to zoom in (a la Prezi) and be able to easily embed it into a web page.

Obvious choice here is to use javascript (web dev, dynamic elements, easily embedable, static web content) and the canvas element seemed like a good starting point. A pinch of w3 schools and now I am well on my way...

  <canvas id="ezbd" width="1200" height="720" style="border:1px solid #000000; background-color: #333;"></canvas>
  <script>

      var data = {
          car: {
              type: "rect",
              color: "red",
              pos: [0, 0, 100, 100],
              carTitle : {
                  type: "text",
                  color: "white",
                  pos: [50, 50],
                  text: "Cars"
              },
              mustang: {
                  label: "Mustang",
                  type: "rect",
                  color: "black",
                  pos: [100, 100, 200, 200],
              },
              camaro: {
                  label: "Camaro",
                  type: "rect",
                  color: "blue",
                  pos: [400, 100, 200, 200],
              },
              mustangCamaro: {
                  label: "Link",
                  type: "line",
                  color: "green",
                  pos: [300, 200, 400, 200],
                  width: 4
              }
          }
      }

      var c = document.getElementById("ezbd");
      var ctx = c.getContext("2d");
      ctx.textAlign = "center";
      ctx.textBaseline = 'middle';
      ctx.font = "24px Arial";

      function recursiveDraw(obj) {
          for (var key in obj) {
              if (typeof obj[key] == "object" && obj[key] !== null) {
                  recursiveDraw(obj[key]);
              } else {
                  // console.log(obj[key]);

                  if (obj[key] == "rect") {
                      ctx.fillStyle = obj.color;
                      ctx.fillRect(obj.pos[0], obj.pos[1], obj.pos[2], obj.pos[3]);

                      if (typeof obj.label !== "undefined") {
                          ctx.fillStyle = "white";
                          ctx.fillText(obj.label, obj.pos[0] + obj.pos[2] / 2, obj.pos[1] + obj.pos[3] / 2);
                      }
                  } else if (obj[key] == "line") {
                      ctx.moveTo(obj.pos[0], obj.pos[1]);
                      ctx.lineTo(obj.pos[2], obj.pos[3]);
                      ctx.strokeStyle = obj.color;
                      ctx.lineWidth = obj.width;
                      ctx.stroke();

                      if (typeof obj.label !== "undefined") {
                          ctx.fillStyle = "white";
                          ctx.fillText(obj.label, (obj.pos[0] + obj.pos[2]) / 2, (obj.pos[1] + obj.pos[3]) / 2);
                      }
                  } else if (obj[key] == "text") {
                      ctx.fillStyle = obj.color;
                      ctx.fillText(obj.text, obj.pos[0], obj.pos[1]);
                  }

              }
          }
      }

      recursiveDraw(data);

  </script>
