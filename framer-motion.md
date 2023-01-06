## 06 January 2023

### How to make on scroll animation with react-intersection-observer

Here is the code snippet 

```js
import { motion, useAnimation } from "framer-motion";
import { useEffect } from "react";
import { useInView } from "react-intersection-observer";

export default function BoxShow() {
  const control = useAnimation();
  const [ref, isBoxInView] = useInView();
  const boxVariants = {
    visible: { opacity: 1, scale: 2 },
    hidden: { opacity: 0, scale: 0 },
  };

  useEffect(() => {
    if (inView) control.start("visible");
    else control.start("hidden");
  }, [isBoxInView, control]);
  
  return (
    <main className="py-10">
      <motion.div className="w-[200px] h-[200px] bg-red-50">
        <span className="text-white">Box 1</span>
      </motion.div>
      
      <motion.div variants={boxVariants} initial="hidden" animate={control} ref={ref} className="w-[200px] h-[200px] bg-red-50">
        <span className="text-white"> Box 1 </span>
      </motion.div>
      
      <motion.div className="w-[200px] h-[200px] bg-red-50">
        <span className="text-white">Box 1</span>
      </motion.div>
    </main>
  );
}
```

here is the explanations

The above code snippet is using react-intersection-observer and framer-motion to animate a box (div) when it is in view (visible to the user) (classNames used above are for tailwindcss)

about the UI we have 3 divs in a parent container and the purpose is to make the box in the middle scale up by the time the user scrolls to it and be hidden when the box is not in view.
To have these animations we are using motion.div which renders a div that can be animated by framer motion
we defined animation variants here

```js
  const boxVariants = {
    visible: { opacity: 1, scale: 2 },
    hidden: { opacity: 0, scale: 0 },
  };

```
this means we have two states the state of hidden where the scale and opacity will be zero (box not visible at all ) and the state visible where it will be bigger and visible

we are then passing these boxVariants into variants props of motion.div so that it can know how to animate our element. By default we want the box to have the hidden state so we specify hidden as the state in the initial prop.By doing this Framer motion will apply the style specified in the hidden variant.

Framer motion provides a hook UseAnimation that can allow us to control our animation and that's where we are using the control object. We pass this control object to the animate prop so that with this control object we can be able to control the animation of the box

Finally, we need a way to know whether our Box is in view or not and that's where we use react-intersection-observer. React intersection observer provides a hook useInView that will used to create the isBoxInView boolean that which will be true when the element is in view and false otherwise and it also provide a ref that we pass to the element we want to observe

in the useEffect we are listenning to when our boolean changes and if the element is inview (isBoxInView true) then we use the control object to trigger visible state and triggle hidden state other wise

and this will achieve our animation
