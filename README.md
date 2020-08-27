# transition

> CSS Transitions 是一个 CSS 模块，定义了如何创建一个平滑地变换 CSS 属性值的方法。它不仅允许创建变换方法，同时也允许通过定时函数来控制变换方法。

## transition CSS 属性

### transition-property

> transition-property 指定应用过渡属性的名称。

语法:

```
/* Keyword values */
transition-property: none;
transition-property: all;
transition-property: test_05;
transition-property: -specific;
transition-property: sliding-vertically;

transition-property: test1;
transition-property: test1, animation4;
transition-property: all, height, all;
transition-property: all, -moz-specific, sliding;

/* Global values */
transition-property: inherit;
transition-property: initial;
transition-property: unset;
```

值:

-   `none`
    没有过渡动画。

-   `all`
    所有可被动画的属性都表现出过渡动画。

-   `IDENT`
    属性名称

可以使用动画的属性参考 [动画 CSS 属性](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties)

### transition-duration

> transition-duration 属性以秒或毫秒为单位指定过渡动画所需的时间。默认值为 0s ，表示不出现过渡动画。

可以指定多个时长，每个时长会被应用到由 transition-property 指定的对应属性上。如果指定的时长个数小于属性个数，那么时长列表会重复。如果时长列表更长，那么该列表会被裁减。两种情况下，属性列表都保持不变。

### transition-delay

> CSS 的 transition-delay 属性规定了在过渡效果开始作用之前需要等待的时间。

值以秒（s）或毫秒（ms）为单位，表明动画过渡效果将在何时开始。取值为正时会延迟一段时间来响应过渡效果；取值为负时会导致过渡立即开始。

### transition-timing-function

> CSS 属性受到 transition effect 的影响，会产生不断变化的中间值，而 CSS transition-timing-function 属性用来描述这个中间值是怎样计算的。实质上，通过这个函数会建立一条加速度曲线，因此在整个 transition 变化过程中，变化速度可以不断改变。

### transition

> transition CSS 属性是 transition-property，transition-duration，transition-timing-function 和 transition-delay 的一个简写属性。
