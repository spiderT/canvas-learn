# canvas-learn

## Demo1: Implement the signature board function

CodePath: /demos/signature.html

![signature](/images/signature.png)

The core is the 2D drawing capability based on Canvas, which listens to the user's mouse or finger movements to complete the corresponding line drawing.

1. To create a smoother transition, use the ctx.quadricCurveTo method.
2. To complete the brush switch, listen for the change event of select and modify the ctx.lineWidth brush accordingly.

```js
function draw(e) {
  e.preventDefault();
  if (!drawing) return;

  const { offsetX, offsetY } = getEventPosition(e);

  // Use a Bezier curve to draw a smooth transition
  ctx.quadraticCurveTo(
    lastX,
    lastY,
    (lastX + offsetX) / 2,
    (lastY + offsetY) / 2
  );
  ctx.stroke();

  lastX = offsetX;
  lastY = offsetY;
}
```
