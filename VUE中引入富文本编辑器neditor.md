# VUE中引入富文本编辑器neditor

####  引入neditor

下载官方文件包,需要梯子,打包文件里有.

文件放在 **public**下

文件目录

--dialogs

​		---是弹窗文件(html),编辑器内部打开弹窗以嵌入ifame,可以**手动更改**

​		---internal.js  如需手动添加弹窗文件,需要将该文件在html**头部引入**.

​								(新增弹窗也**可以用element实现**,)

--i18n

​		---zh-cn

​			----zh-cn.js  在**不使用三方框架时**,添加按钮,需要在 labelMap数组尾部添加相应描述,								格式为 **'name':'提示文字'**

​								(新增按钮可以在vue内部添加数组对象)

--themes

​		---存储样式主题文件(css,img)

​				----notadd

​							---css 如果修改原始样式,编辑neditor.css即可

​							

```css
//使用css变量,实现主题色
:root{
    --theme-color:#409eff;
    --theme-color-hover:#66b1ff;
}
//使用方式
.aaa{
    color:var(--theme-color,#409eff)  //填入#409eff是默认颜色,即 
        --theme-color? --theme-color :#409eff
}

```



​							---images图片文件

--index.html 演示完整demo

--neditor.all.js 编辑器源码

--neditor.config.js 编辑器配置项  ,vue引入时,参数配置参考该文件

#### vue文件内使用

引入`import VueNeditorWrap from "vue-neditor-wrap";`

组件注册` components: {VueNeditorWrap },`

```vue
 <vue-neditor-wrap
       // ref="neditor"
        :init="init"   //初始化执行该函数,添加按钮事件等
        v-model="content"
        :config="myConfig"   //配置参数
        :destroy="false"
        @ready="ready" //  编辑器初始化完毕后执行该函数
      ></vue-neditor-wrap>
```

data内存放数据

```js
   myConfig: {
        // 如果需要上传功能,找后端小伙伴要服务器接口地址
        serverUrl: "/api/web/upload/ueditor",
        // 你的UEditor资源存放的路径,相对于打包后的index.html
        UEDITOR_HOME_URL: "/NEditor/",
        // 编辑器不自动被内容撑高
        autoHeightEnabled: false,
        // 初始容器高度
        initialFrameHeight: 240,
        // 初始容器宽度
        initialFrameWidth: "100%",
        // 关闭自动保存
        enableAutoSave: false,
        toolbars: [  //渲染按钮用, 添加按钮需要先在此添加
          [
            "source", // 源代码
            "undo", // 撤销
            "redo", // 重做
            "|",
            "insertcode", // 代码语言
            "fontfamily", // 字体
            "fontsize", // 字号
            "bold", // 加粗
            "italic", // 斜体
            "underline", // 下划线
            "forecolor", // 字体颜色
            "backcolor", // 背景色
            "removeformat", // 清除格式
            "autotypeset", // 自动排版
            "indent", // 首行缩进
            "pasteplain", // 纯文本粘贴模式
            "formatmatch", // 格式刷
            "|",
            "justifyleft", // 居左对齐
            "justifyright", // 居右对齐
            "justifycenter", // 居中对齐
            "justifyjustify", // 两端对齐
            "insertorderedlist", // 有序列表
            "insertunorderedlist", // 无序列表
            "rowspacingtop", // 段前距
            "rowspacingbottom", // 段后距
            "lineheight", // 行间距
            "link", // 超链接
            "unlink", // 取消链接
            "simpleupload", // 单图上传
            "insertimage", // 多图上传
            "insertvideo", // 视频
            "music", // 音乐
            "attachment", // 附件上传
            "wordimage", // 图片转存
            "pagebreak", // 分页
            "inserttable", // 插入表格
            "searchreplace", // 查询替换
            "|",
            "fullscreen", // 全屏
            "imagecenter", // 居中
            "anchor", // 锚点
            "snapscreen", // 截图
            "strikethrough", // 删除线
            "subscript", // 下标
            "fontborder", // 字符边框
            "superscript", // 上标
            "blockquote", // 引用
            "selectall", // 全选
            "print", // 打印
            "preview", // 预览
            "horizontal", // 分隔线
            "time", // 时间
            "date", // 日期
            "insertrow", // 前插入行
            "insertcol", // 前插入列
            "mergeright", // 右合并单元格
            "mergedown", // 下合并单元格
            "deleterow", // 删除行
            "deletecol", // 删除列
            "splittorows", // 拆分成行
            "splittocols", // 拆分成列
            "splittocells", // 完全拆分单元格
            "deletecaption", // 删除表格标题
            "inserttitle", // 插入标题
            "mergecells", // 合并多个单元格
            "deletetable", // 删除表格
            "cleardoc", // 清空文档
            "insertparagraphbeforetable", // "表格前插入行"
            "paragraph", // 段落格式
            "edittable", // 表格属性
            "edittd", // 单元格属性
            "emotion", // 表情
            "spechars", // 特殊字符
            "map", // Baidu地图
            "gmap", // Google地图
            "help", // 帮助
            "directionalityltr", // 从左向右输入
            "directionalityrtl", // 从右向左输入
            "insertframe", // 插入Iframe
            "imagenone", // 默认
            "imageleft", // 左浮动
            "imageright", // 右浮动
            "attachment", // 附件
            "edittip ", // 编辑提示
            "customstyle", // 自定义标题
            "webapp", // 百度应用
            "touppercase", // 字母大写
            "tolowercase", // 字母小写
            "background", // 背景
            "template", // 模板
            "scrawl", // 涂鸦
            "drafts", // 从草稿箱加载
            "charts", // 图表,
            "cusbtn",
            "newdialog",
            "newbtn",
          ],
        ],
      },
      UE: {},
      content: "",
          //按钮接受三个参数,tip相当于title属性, handler是事件
      buttons: [
        {
          name: "newbtn",
          tip: "上传图片",
          handler:function () {
           this.centerDialogVisible=true
          }.bind(this)    //用箭头函数则不需要绑定this
        },
        {
          name: "newdialog",
          tip: "上传图片234234",
          handler:function () {
            var iframe =document.querySelector(" .edui-editor-iframeholder iframe").contentWindow
            // console.log(iframe.document.querySelectorAll("body.view img"));
          iframe.document.querySelectorAll("body.view img").forEach((cur)=>{
            console.log(cur);
          cur.src= "https://pic.cr173.com/up/2016-1/2016010515195526477.jpg"
          })
          }.bind(this)
        },
      ],
      wordBtn: {
        name: "wordimage",
        tip: "文件导入",
        handler(editor, name) {
          console.log(editor, name);
          document.querySelector(".word-uploader input").click();
        },
      },
          
```

method

```js
 methods: {
    test() {
      console.log("测试函数");
    },
    init() {
   // this.$refs.neditor.registerButton 是个函数,主要用于注册组件
       if (this.$refs.neditor) {
        this.buttons.forEach(this.$refs.neditor.registerButton);
      }
    },

    ready(editor) {
      this.UE = editor
      console.log("初始化完成");
      
    },
  },
```

添加按钮流程

在data中  `toolbar`  添加,按钮name,在按照`buttons`格式创建一组按钮,

在method `init`函数内注册

#### 修改样式

```html
<style>
// 修改icon大小
.edui-notadd .edui-toolbar .edui-button  .edui-icon {
  font-size: 20px;
  color: #777;
}
// 修改icon
.edui-for-newbtn .edui-icon {
  background: url("../../public/工具.png") no-repeat center;
  background-size: contain;
}
.edui-for-newdialog .edui-icon {
  background: url("../../public/工具.png") no-repeat center;
  background-size: contain;
}
</style>
```

