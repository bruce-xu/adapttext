# 高度自适应的 textarea 文本输入框

使文本输入框 textarea 随着用户输入自适应高度

默认情况下 textarea 的高度是固定的，不会随着内容变化而变化。内容过多时会出现滚动条。有时候会希望随着内容的增多，textarea 自动增加高度，从而不出现滚动条。本脚本用于实现此功能。思路来源于网上。大致过程如下：在 textarea 的外面包裹一个 div 元素，同时在 textarea 的同一级增加一个 pre 元素。利用 pre 的特性：内容会保留格式，且高度会随着内容高度的变化而变化。先通过 `visibility: hidden` 将其隐藏，但其仍然占据页面空间。通过 pre 来影响外层 div的大小。同时设置 textarea 基于 外层 div 绝对定位，其 width、height 都设置为 100%。最后，设置 textarea 的input 事件，使其输入内容时，动态将 textarea 的内容赋予 pre，使 pre 的文本内容和 textarea 的输入值保持同步。于是，pre 的大小决定了外层 div 的大小，div 的大小决定了 textarea 的大小，而 textarea 的内容变化时又会动态改变 pre 的内容，从而改变它的大小。因此形成了一个环，从而实现了 textarea 的高度随输入变化而变化的需求。

使用：

    var textarea = document.getElementById('textarea');
    AdaptText(textarea);
    
    OR
    AdaptText({
        textarea: textarea
    });
    
    OR
    AdaptText({
        textarea: textarea,
        minHeight: 50,
        maxHeight: 500
    });

Demo：
[textarea 高度自适应 Demo](http://bruce-xu.github.io/demos/adapttext/)
