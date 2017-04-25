# vue-uploader

> A Vue.js project

当前版本使用张鑫旭老师的 [基于HTML5的可预览多图片Ajax上传](http://www.zhangxinxu.com/wordpress/2011/09/%E5%9F%BA%E4%BA%8Ehtml5%E7%9A%84%E5%8F%AF%E9%A2%84%E8%A7%88%E5%A4%9A%E5%9B%BE%E7%89%87ajax%E4%B8%8A%E4%BC%A0/) 
致谢!

重难点：

1. `FileList` 是一个对象，同时又有数组属性，里面有多个 `File` 对象，因为 `FileList` 对象是只读不可修改的
`files.splice is not a function`
所以如果需要在上传前对多文件进行增删操作，就需要建立一个空数组，把每个 `File Object` 加进去，对这个数组进行修改

2. 使用for循环添加onload顺序会乱,疑似 `FileReader()` 是异步操作

3. 在上传文件之前需要清空文件预览，否则 `fileFilter` 与 `filePreview` 的内容会不对应。原因为input的change事件为先清空input的value再填充value

4. 上传后清空 `fileFilter` 未使用原方法

5. 从第一张开始删除未上传的文件，导致File index混乱，需要在删除文件后更新视图

Note：

1. 查询得知文件大类有如下几种：application、text、drawing、audio、Model、image、java、message、multipart、message、

2. 部分文件在浏览器中可能不能正确识别 `fileType` ，比如apk文件

3. 使用浏览器 `原生xhr` ，易于获取控制上传进度，但只支持IE10+

4. 上传部分使用 `(function(file) {xxxx})(file);` 立即执行函数

未实现的部分：

0. 图片压缩

1. 上传文件总进度

2. 其他格式文件上传预置预览

3. 多次添加同一文件未做比对

4. 组件化

5. 取消上传按钮 按钮优化

6. 文件总数限制

7. 拖拽文件

8. props:[count,width,uploadUrl,showName]

<p data-height="512" data-theme-id="dark" data-slug-hash="NjNBWo" data-default-tab="html,result" data-user="shoyuf" data-embed-version="2" data-pen-title="demo" data-preview="true" class="codepen">See the Pen <a href="https://codepen.io/shoyuf/pen/NjNBWo/">demo</a> by shoyuVan (<a href="http://codepen.io/shoyuf">@shoyuf</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>