# CSS3 动画

> CSS Animations 是 CSS 的一个模块，它定义了如何用关键帧来随时间推移对 CSS 属性的值进行动画处理。关键帧动画的行为可以通过指定它们的持续时间，它们的重复次数以及它们如何重复来控制。

## animation css 属性

### animation-name

> animation-name 属性指定应用的一系列动画，每个名称代表一个由@keyframes 定义的动画序列。

语法:

`animation-name: none/keyframes name;`

### animation-duration

> animation-duration 属性指定一个动画周期的时长。默认值为 0s，表示无动画。

语法:

`animation-duration:time`

一个动画周期的时长，单位为秒(s)或者毫秒(ms)，无单位值无效。

注意：负值无效，浏览器会忽略该声明，但是一些早起的带前缀的声明会将负值当作 0s。

### animation-fill-mode

> CSS 属性 animation-fill-mode 设置 CSS 动画在执行之前和之后如何将样式应用于其目标。

语法:

```
/* Single animation 单动画 */
animation-fill-mode: none;
animation-fill-mode: forwards;
animation-fill-mode: backwards;
animation-fill-mode: both;

/* Multiple animations 多动画 */
animation-fill-mode: none, backwards;
animation-fill-mode: both, forwards, none;
```

值:

-   `none` 当动画未执行时，动画将不会将任何样式应用于目标，而是已经赋予给该元素的 CSS 规则来显示该元素。这是默认值。

-   `forwards` 目标将保留由执行期间遇到的**最后一个关键帧**计算值,最后一个关键帧取决于`animation-direction`和`animation-iteration-count`的值：

-   `backwards` 动画将在应用于目标时立即应用第一个关键帧中定义的值，并**在`animation-delay`期间保留此值**。 第一个关键帧取决于`animation-direction`的值：

-   `both`动画将遵循`forwards`和`backwards`的规则，从而在两个方向上扩展动画属性。

### animation-delay

> animation-delay CSS 属性定义动画于何时开始，即从动画应用在元素上到动画开始的这段时间的长度。(就是延迟时间)

语法:

```
animation-delay: 3s;
animation-delay: 2s, 4ms;
```

值:

-   `time` 从动画样式应用到元素上到元素开始执行动画的时间差。该值可用单位为秒(s)和毫秒(ms)。如果未设置单位，定义无效。

### animation-iteration-count

> animation-iteration-count CSS 属性 定义动画在结束前运行的次数 可以是 1 次 无限循环.如果指定了多个值，每次播放动画时，将使用列表中的下一个值，在使用最后一个值后循环回第一个值。

### animation-direction

> animation-direction CSS 属性指示动画是否反向播放，它通常在简写属性 animation 中设定

语法:

`single-animation-direction = normal | reverse | alternate | alternate-reverse`

```
animation-direction: normal
animation-direction: reverse
animation-direction: alternate
animation-direction: alternate-reverse
animation-direction: normal, reverse
animation-direction: alternate, reverse, normal
```

值:

+ `normal`
每个循环内动画向前循环，换言之，每个动画循环结束，动画重置到起点重新开始，这是默认属性。

+ `alternate`
动画交替反向运行，反向运行时，动画按步后退，同时，带时间功能的函数也反向，比如，ease-in 在反向时成为ease-out。计数取决于开始时是奇数迭代还是偶数迭代

+ `reverse`
反向运行动画，每周期结束动画由尾到头运行。

+ `alternate-reverse`
反向交替， 反向开始交替

### animation-timing-function

> CSS animation-timing-function属性定义CSS动画在每一动画周期中执行的节奏。可能值为一或多个timing-function。

### animation-play-state

> `animation-play-state` CSS 属性定义一个动画是否运行或者暂停。可以通过查询它来确定动画是否正在运行。另外，它的值可以被设置为暂停和恢复的动画的重放。

```
animation-play-state: running;
animation-play-state: paused;

/* Multiple animations */
animation-play-state: paused, running, running;

/* Global values */
animation-play-state: inherit;
animation-play-state: initial;
animation-play-state: unset;
```

## animation 规则 --> 关键帧 @keyframes

> 关键帧 `@keyframes` at-rule 规则通过在动画序列中定义关键帧（或 waypoints）的样式来控制 CSS 动画序列中的中间步骤。和 转换 `transition` 相比，关键帧 keyframes 可以控制动画序列的中间步骤。

```
@keyframes slidein {
  from {
    transform: translateX(0%);
  }

  to {
    transform: translateX(100%);
  }
}
```

JavaScript 可以通过 CSS 对象模型的 [CSSKeyframesRule](https://developer.mozilla.org/zh-CN/docs/Web/API/CSSKeyframesRule) 接口来访问 @keyframes。

要使用关键帧, 先创建一个带名称的 @keyframes 规则，以便后续使用 animation-name 属性将动画同其关键帧声明匹配。每个 @keyframes 规则包含多个关键帧，也就是一段样式块语句，每个关键帧有一个百分比值作为名称，代表在动画进行中，在哪个阶段触发这个帧所包含的样式。

可以按任意顺序列出关键帧百分比；它们将按照其应该发生的顺序来处理。

> 让关键帧序列生效

如果一个关键帧规则没有指定动画的开始或结束状态（也就是，`0%/from 和100%/to`，浏览器将使用元素的现有样式作为起始/结束状态。这可以用来从初始状态开始元素动画，最终返回初始状态。

如果在关键帧的样式中使用了不能用作动画的属性，那么这些属性会被忽略掉，支持动画的属性仍然是有效的，不受波及。

> 重复定义

如果多个关键帧使用同一个名称，以最后一次定义的为准。 `@keyframes` 不存在层叠样式(cascade)的情况，所以动画在一个时刻（阶段）只会使用一个的关键帧的数据。

如果一个`@keyframes` 里的**关键帧的百分比存在重复的情况，以最后一次定义的关键帧为准**。 因为`@keyframes` 的规则不存在层叠样式(cascade)的情况，即使多个关键帧设置相同的百分值也不会全部执行。

> 属性个数不定

如果一个关键帧中没有出现其他关键帧中的属性，那么这个属性将使用插值（不能使用插值的属性除外，这些属性会被忽略掉）。例如：

```
@keyframes identifier {
  0% { top: 0; left: 0; }
  30% { top: 50px; }
  68%, 72% { left: 50px; }
  100% { top: 100px; left: 100%; }
}
```

例子中，top 属性分别出现在关键帧 0%、30% 和 100% 的中，而 left 属性分别出现在关键帧 0%、68%、72% 和 100% 中。

> 同一关键帧中的相同属性被重复定义
> 如果某一个关键帧出现了重复的定义，且重复的关键帧中的 CSS 属性值不同，则以最后一次定义的属性为准。例如：

```
@keyframes identifier {
  0% { top: 0; }
  50% { top: 30px; left: 20px; }
  50% { top: 10px; }
  100% { top: 0; }
}
```

上面这个例子中，50% 关键帧中分别最后设置的属性 top: 10px 和 left: 20px 是有效的，但是其他的属性会被忽略。

Firefox 14 开始支持层叠 keyframes。

> 关键帧中的 !important
> 关键帧中出现的 !important 将会被忽略。

```
@keyframes important1 {
  from { margin-top: 50px; }
  50%  { margin-top: 150px !important; } /* 忽略 */
  to   { margin-top: 100px; }
}

@keyframes important2 {
  from { margin-top: 50px;
         margin-bottom: 100px; }
  to   { margin-top: 150px !important; /* 忽略 */
         margin-bottom: 50px; }
}
```

##
