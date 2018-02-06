```
sweetalert2.min.css
```

SweetAlert2是一款功能强大的纯Js模态消息对话框插件。SweetAlert2用于替代浏览器默认的弹出对话框，它提供各种参数和方法，支持嵌入图片，背景，HTML标签等，并提供5种内置的情景类，功能非常强大。

SweetAlert2是SweetAlert-js的升级版本，它解决了SweetAlert-js中不能嵌入HTML标签的问题，并对弹出对话框进行了优化，同时提供对各种表单元素的支持，还增加了5种情景模式的模态对话框。

### 安装

可以通过bower或npm来安装sweetalert2对话框插件。

| 12 | `bower install sweetalert2npm install sweetalert2` |
| :--- | :--- |




### 使用方法

使用SweetAlert2对话框需要在页面中引入sweetalert2.min.css和sweetalert2.min.js文件，为了兼容IE浏览器，还需要引入promise.min.js文件。

| 1234 | `<link rel="stylesheet"type="text/css"href="path/to/sweetalert2/dist/sweetalert2.min.css"><script src="path/to/sweetalert2/dist/sweetalert2.min.js"></script><!--forIE support --><script src="path/to/es6-promise/promise.min.js"></script>` |
| :--- | :--- |




##### 基本使用

最基本的使用方法是通过`swal()`来弹出一个对话框。

| 1 | `swal('Hello world!');` |
| :--- | :--- |




如果要弹出一个带情景模式的对话框，可以在的第二个参数中设置。

| 1 | `swal('Oops...','Something went wrong!','error');` |
| :--- | :--- |




你可以通过下面的方法来处理对话框的用户交互：

| 123456789101112131415161718192021222324252627 | `swal({title:'Are you sure?',text:'You will not be able to recover this imaginary file!',type:'warning',showCancelButton:true,confirmButtonText:'Yes, delete it!',cancelButtonText:'No, keep it',}).then(function(isConfirm) {if(isConfirm ===true) {swal('Deleted!','Your imaginary file has been deleted.','success');}elseif(isConfirm ===false) {swal('Cancelled','Your imaginary file is safe :)','error');}else{// Esc, close button or outside click// isConfirm is undefined}}); ` |
| :--- | :--- |




`swal(...)`会返回一个Promise对象，该Promise对象中`then`方法中的`isConfirm`参数的含义如下：

* `true`
  ：代表Confirm（确认）按钮。
* `false`
  ：代表Cancel（取消）按钮。
* `undefined`
  ：代表按下Esc键，点击取消按钮或在对话框之外点击。

##### 模态对话框的类型

sweetalert2提供了5种情景模式的对话框。

![](https://images2015.cnblogs.com/blog/841651/201611/841651-20161108093244280-181355543.png)

### 配置参数

| 参数 | 默认值 | 描述 |
| :--- | :--- | :--- |
| title | null | 模态对话框的标题。它可以在参数对象的`title`参数中设置，也可以在`swal()`方法的第一个参数设置。 |
| text | null | 模态对话框的内容。它可以在参数对象的`text`参数中设置，也可以在`swal()`方法的第二个参数设置。 |
| html | null | 对话框中的内容作为HTML标签。如果同时提供`text`和`html`参数，插件将会优先使用`text`参数。 |
| type | null | 对话框的情景类型。有5种内置的情景类型：`warning`，`error`，`success`，`info`和`question`。它可以在参数对象的`type`参数中设置，也可以在`swal()`方法的第三个参数设置。 |
| customClass | null | 模态对话框的自定义class类。 |
| animation | true | 如果设置为false，对话框将不会有动画效果。 |
| allowOutsideClick | true | 是否允许点击对话框外部来关闭对话框。 |
| allowEscapeKey | true | 是否允许按下Esc键来关闭对话框。 |
| showConfirmButton | true | 是否显示“Confirm（确认）”按钮。 |
| showCancelButton | false | 是否显示“Cancel（取消）”按钮。 |
| confirmButtonText | "OK" | 确认按钮上的文本。 |
| cancelButtonText | "Cancel" | 取消按钮上的文本。 |
| confirmButtonColor | "\#3085d6" | 确认按钮的颜色。必须是HEX颜色值。 |
| cancelButtonColor | "\#aaa" | 取消按钮的颜色。必须是HEX颜色值。 |
| confirmButtonClass | null | 确认按钮的自定义class类。 |
| cancelButtonClass | null | 取消按钮的自定义class类。 |
| buttonsStyling | true | 为按钮添加默认的swal2样式。如果你想使用自己的按钮样式，可以将该参数设置为false。 |
| reverseButtons | false | 如果你想反向显示按钮的位置，设置该参数为true。 |
| showLoaderOnConfirm | false | 设置为true时，按钮被禁用，并显示一个在加载的进度条。该参数用于AJAX请求的情况。 |
| preConfirm | null | 在确认之前执行的函数，返回一个Promise对象。 |
| imageUrl | null | 为模态对话框自定义图片。指向一幅图片的URL地址。 |
| imageWidth | null | 如果设置了`imageUrl`参数，可以为图片设置显示的宽度，单位像素。 |
| imageHeight | null | 如果设置了`imageUrl`参数，可以为图片设置显示的高度，单位像素。 |
| imageClass | null | 自定义的图片class类。 |
| timer | null | 自动关闭对话框的定时器，单位毫秒。 |
| width | 500 | 模态窗口的宽度，包括padding值（`box-sizing: border-box`）。 |
| padding | 20 | 模态窗口的padding内边距。 |
| background | "\#fff" | 模态窗口的背景颜色。 |
| input | null | 表单input域的类型，可以是"text", "email", "password", "textarea", "select", "radio", "checkbox" 和 "file"。 |
| inputPlaceholder | "" | input域的占位符。 |
| inputValue | "" | input域的初始值。 |
| inputOptions | {} 或 Promise | 如果`input`的值是`select`或`radio`，你可以为它们提供选项。对象的key代表选项的值，value代表选项的文本值。 |
| inputAutoTrim | true | 是否自动清除返回字符串前后两端的空白。 |
| inputValidator | null | 是否对input域进行校验，返回Promise对象。 |
| inputClass | null | 自定义input域的class类。 |

你可以使用`swal.setDefaults(customParams)`方法来覆盖默认的参数，`customParams`是一个对象。

### 方法

| 方法 | 描述 |
| :--- | :--- |
| swal.setDefaults\({Object}\) | 当你在使用SweetAlert2时有大量的自定义参数，可以通过`swal.setDefaults({Object})`方法来将它们设置为默认参数。 |
| swal.resetDefaults\(\) | 重置设置的默认值。 |
| swal.queue\(\[Array\]\) | 提供一个数组形式的SweetAlert2参数，用于显示多个对话框。对话框将会一个接一个的出现。 |
| swal.close\(\) 或 swal.closeModal\(\) | 以编程的方式关闭当前打开的SweetAlert2对话框。 |
| swal.enableButtons\(\) | 确认和关闭按钮可用。 |
| swal.disableButtons\(\) | 禁用确认和关闭按钮。 |
| swal.enableLoading\(\) 或 swal.showLoading\(\) | 禁用按钮并显示加载进度条。通常用于AJAX请求。 |
| swal.disableLoading\(\) 或 swal.hideLoading\(\) | 隐藏进度条并使按钮可用。 |
| swal.clickConfirm\(\) | 以编程的方式点击确认按钮。 |
| swal.clickCancel\(\) | 以编程的方式点击取消按钮。 |
| swal.showValidationError\(error\) | 显示表单校验错误信息。 |
| swal.resetValidationError\(\) | 隐藏表单校验错误信息。 |
| swal.enableInput\(\) | 使input域可用。 |
| swal.disableInput\(\) | 禁用input域。 |

### 浏览器兼容

SweetAlert2可以工作在所有的现代浏览器中：

* IE: 10+（需要引入Promise文件）
* Microsoft Edge: 12+
* Safari: 4+
* Firefox: 4+
* Chrome 14+
* Opera: 15+

SweetAlert2模态对话框插件的github地址为：[https://github.com/limonte/sweetalert2](https://github.com/limonte/sweetalert2)

学习是一个不断抄袭和重复的过程.

