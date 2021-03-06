# vertical-align

# 作用

用来指定行内元素或表格单元格元素的垂直对齐方式

# 基本语法

对于行内样式

| 值 | 效果 |
| ---| --- |
| baseline | 元素基线与父元素的基线对齐 |
| sub      | 元素基线与父元素的下标基线对齐 | 
| super    | 元素基线与父元素的上标基线对齐 |
| text-top | 元素顶端与父元素字体的顶端对齐 | 
| text-bottom | 元素底端与父元素字体的底端对齐 | 
| middle   | 元素中垂线与(父元素的基线加上小写x一半的高度值对齐) | 
| top      | (元素及后代的顶端)与整行的顶端对齐 |
| bottom   | (元素及后代的顶端)与整行的底端对齐 | 
| 具体length | 元素基线超过父元素的基线指定高度 可取值为负数 |
| 具体百分比  | 具体值为 line-height * 百分比 | 

具体的效果

可见: https://cssreference.io/property/vertical-align/#vertical-align

对于table-cell元素

| 值 | 效果 | 
| --- | --- |
| 其余值 | 与同行单元格的基线对齐 |
| middle | 单元格垂直居中 | 
| bottom | (单元格的内边距的下边缘)与行的底端对齐 |