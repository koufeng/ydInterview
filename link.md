# link 引用资源页面渲染影响

`<link>`标签不会阻塞DOM解析但会阻塞DOM渲染

`<link>` 标签会阻塞js的执行

`<script>`标签会阻塞DOM的解析和渲染；

`<link>`标签并不会像带scr属性的`<script>`标签一样会触发页面paint。浏览器并行解析生成DOM` Tree 和 CSSOM Tree，当两者都解析完毕，才会生成rending tree，页面才会渲染。所以应尽量减小引入样式文件的大小，提高首屏展示速度。

`<script>`标签会阻塞DOM解析和渲染，但在阻塞同时，其他线程会解析文档的其余部分（预解析），找出并加载需要通过网络加载的其他资源。通过这种方式，资源可以在并行连接上加载，从而提高总体速度。预解析不会修改解析出来的 DOM 树，只会解析外部资源（例如外部脚本、样式表和图片）的引用。

## 优化

- 合理放置脚本位置
- 预加载 `Link preload`
- `DNS Prefetch` 预解析
- `script` 延迟脚本加载 `defer/async`
