# keyframes

## Animations vs Transitions

`Animations` let you animate elements from one style configuration to another.

`Transitions` were designed to animate an element from one state to another. They can loop, but they weren’t designed for that. Animations, on the other hand, were designed with the purpose of explicitly enabling loops.

`Transitions` need a trigger, such as the use of pseudo-classes like `:hover` or `:focus`, or by adding/removing a class via JavaScript. Animations, on the other hand, do not need such a trigger. Once you have your elements in place and CSS defined, an animation will start running immediately if that’s what you told it to do

`Transitions` are not as flexible as using animations. When you define a transition, imagine you are sending that element on a journey in a straight line from point A to point B. Yes, the `transition-timing-function` can add some variation to the timing of this change, but it doesn’t compare to the amount of flexibility added by using animations.

All in all, both animations and transitions have their use, so in addition to considering the above differences you should also use your best judgement. For example, if you need to change the opacity of an element when it is active then an animation would be overkill, but if you need to carry out something more complicated, animations will provide you with the tools you need.

## Animation Properties

```css
#ball {
  /* ... other CSS properties ... */
  animation-duration: 2s;
  animation-name: change-color;
  animation-iteration-count: infinite;
  animation-direction: alternate;
}
```

* An `animation-duration` of two seconds. This means that it will take two seconds for the `#ball` element to complete one animation cycle.

* Defined the `animation-name` to be “change-color” which is essential for the `@keyframes` section coming up next. This is just a custom name that is not a particular CSS value. We could have called it “pineapples” if we so wished, but for our purposes “change-color” suits well.

* Set the `animation-iteration-count` to `infinite`, which means this animation will run forever. You could set this to 1, 2, or as many iterations as you wish.

* Set the `animation-direction` to `alternate`. This property decides if our animation should alternate direction on the completion of one cycle, or reset to the start point and repeat itself. Here it means that the `#ball` will smoothly change back to it’s original color instead of “jumping” straight back to red.

## Keyframes

```css
@keyframes change-color {
  from {
    background-color: red;
  }

  to {
    background-color: green;
  }
}
```

We use the `from` and `to` properties to change the `background-color`

It’s important to know that keyframes use a percentage to indicate the times for an animation to take place and that the `from` and `to` statements are actually aliases for `0%` and `100%`, respectively. You can read `from/0%` as meaning ‘at zero seconds’ and `to/100%` as ‘at 2 seconds’ according to our `animation-duration` in our example from above. There is no hard and fast rule on whether or not you should use `from/to` or `0%/100%`. Just pick a style and be consistent with it.

```css
#ball {
  /* ... other CSS properties ... */
  background-color: red;
  animation: 2s change-color infinite alternate;
}

@keyframes change-color {
  from {
    background-color: red;
  }
  
  50% {
    width: 200px;
    height: 200px;
    background-color: blue;
  }

  to {
    background-color: green;
  }
}
```