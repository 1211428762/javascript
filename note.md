# 第一章

## 1.1 js组成

|                  |        JavaScript        |                                |
| ---------------- | :----------------------: | ------------------------------ |
| ECMAscipt        |           BOM            | DOM                            |
| 提供核心语言功能 | 与浏览器交互的方法与接口 | 访问和操作网页内容的方法和接口 |

# 第二章

## 2.1 script标签

- `<srcipt async="async"> 立即下载脚本,不妨碍页面的其他操作,只对外部脚本有效.`

- `<srcipt defer="defer"> 在<html>后面解析,延迟解析,只对外部脚本有效.`

- <script type="text/javascript" src="test.js"></script>

<script></script>加了src属性后即便在标签内写脚本也不会解析.放在</body>前面,利用页面快速加载

**<noscipt>只有不支持脚本或者禁用脚本时才显示</noscript>**