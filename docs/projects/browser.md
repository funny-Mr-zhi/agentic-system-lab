# Toy Browser Engine

目标：实现从 URL/HTML 到 DOM、CSSOM、layout、paint、event loop 的最小浏览器内核。

参考项目：

- Robinson: https://github.com/mbrubeck/robinson
- Web Browser Engineering: https://github.com/browserengineering/book
- Servo: https://github.com/servo/servo
- Ladybird: https://github.com/LadybirdBrowser/ladybird

## Milestones

### M1: HTML And DOM

实现：

- tokenizer
- parser
- DOM tree
- text nodes
- simple error recovery

必须能解释：

- HTML 为什么不是普通 XML？
- parser 如何处理不闭合标签？
- DOM node 和 layout box 为什么不是一回事？

### M2: CSS And Style

实现：

- selector parsing
- specificity
- cascade
- inherited properties
- computed style

Codex 任务：

```text
请为 CSS specificity 和 cascade 设计测试样例。
覆盖 id/class/tag、source order、inheritance、unknown property。
```

### M3: Layout

实现：

- block layout
- inline text layout
- box model
- viewport
- scroll

先不要做 flex/grid。把 block layout 写清楚比功能堆多更重要。

### M4: Paint And Compositing

实现：

- display list
- rasterization
- clipping
- invalidation
- screenshot regression

### M5: Script And Event Loop

实现：

- tiny JS binding 或嵌入现成 JS engine
- DOM mutation
- click/key events
- timer
- task queue

## Completion

完成时你应该能解释：浏览器不是“把 HTML 画出来”，而是解析、样式计算、布局、绘制、事件循环、安全隔离和增量更新之间的复杂协作。
