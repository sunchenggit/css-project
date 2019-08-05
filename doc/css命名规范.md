# CSS 命名规范

## 前台

### 规则

1. `CSS` 嵌套书写不能超过三层
2. `html` 采用 `h5` 的标签来写
3. 文字单位采用 `px` 结合 `em` 来写
4. 框架单位用 `%` ，在 `scss` 中采用 `percentage(A / B)` 函数来写

### 前缀

1. 通用前缀 `xy-` 
2. 被 `js` 使用的 `DOM` 元素 `js-`



### 组织

1. 全局样式重置使用 `Normalize.css` ，自己需要额外添加的 `reset.css`

2. 功能性的样式都写在通用的类型里。(需要自己新建 `common.css` )例：某个元素需要加粗 `<div class="text-bold"></div>`

   - 文字加粗 `text-bold`
   - 文字截取 `text-crop`
   - 左浮动 ` box-left` 
   - 右浮动 `box-right`
   - 内边距 `pa-`，上边距 `pt-`，下边距`pb-`，左边距 `pl-`，右边距 `pr-`，上下边距 `ptb-`，左右边距 `plr-`
   - 外边距 `ma-0`，上边距 `mt-`，下边距 `mb-`，左边距 `ml-`，右边距 `mr-`，上下边距 `mtb-`，左右边距 `mlr-`
   - 边框弧度 `border-radius-`
   - ...
   - 这里可扩展性太多还可以细分，后期完善

3. 各个模块的命名

   - 最外层模块用模块所代表的的含义命名。例：
     - banner： `<section class="xy-banner"></section>`
     - 产品： `<section class="xy-product"></section>`
   - 内部细分：
     - 可视范围：`<div class="xy-container"></div>`
     - 当前模块的标题(一般样式都是一样的，所以可以用通用的命名，如果有不一样的可以在以模块名细分)：`<div class="xy-title xy-product-title"></div>`
     - 其他部分类似 ...

4. 布局的样式和图文的样式需要抽离。例：

   - 产品列表的布局

     ```html
     <!-- html -->
     <ul class="xy-product-row xy-ptoduct-style ptb-20">
         <li class="col-md-6"><a href='javascript:;'>
         	<div class="img"><img src="" /></div>    
             <h3>产品标题</h3>
         </a></li>
     </ul>
     
     <!-- style -->
     <style>
         /* 外层布局采用 bs 的样式，如果间距不对的话，自己写样式来替换 bs 的默认的样式 */
         .xy-product-row div[class^='col-'] {}
         
         /* 内部元素的样式单独抽出来书写，当外层布局改掉的时候，内部元素的样式是不变的，从而实现可复用性， */
         .xy-ptoduct-style a {}
         .xy-ptoduct-style .img {}
         .xy-ptoduct-style h3 {}
     </style>
     ```

     

## 后台