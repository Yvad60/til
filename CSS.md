### Clip path with polygon path

The clip path is use to specify which apart of the element to display and the rest parts get clipped away

syntax:

```css
clip-path: polygon(x y, x y, x y, x y);
```

the `x` and `y` in this case means the border points of the path on the left, right, top and button (moving clockwise): note that the polygon can have more or less sides not limited to only 4

confusing? :)

Example:

```
clip path: polygon(50% 0, 100% 50%, 50% 100%, 0 50%)
```
The above clip path will create a diamond shaped path here is what the polygon parameter mean

`50% 0`: here 50% is the x and 0 is the y this mean on the left the point will be on 50% of the x axis and 0 (right on the edge) of the Y axis
