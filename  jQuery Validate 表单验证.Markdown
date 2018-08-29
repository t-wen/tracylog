# jQuery Validate 表单验证

jQuery Validate 插件为表单提供了强大的验证功能，让客户端表单验证变得更简单，同时提供了大量的定制选项，满足应用程序各种需求。该插件捆绑了一套有用的验证方法，包括 URL 和电子邮件验证，同时提供了一个用来编写用户自定义方法的 API。所有的捆绑方法默认使用英语作为错误信息，且已翻译成其他 37 种语言。

## 验证流程 
- **首先将我们要用的三个插件写入本路径**
- 
- **插件：jQuery.js**
- **插件：jQuery.validate.js**
- **jQuery.validate的配置文件：messages.js**
- **然后编写表单页面html**
- 
- **html：index.html**


-------------------

## 实现表单验证的步骤

 - 首先，我们建立一个文件夹 jQuery_project
 - jQuery.js 我们可以到 jQuery 官网查找源文件，然后将其下载到我们当前文件夹jQuery_project下就ok了。
 - 同样 jQuery.validate.js 我们可以到  jQuery.validate 官网下载其源文件到文件夹jQuery_project，并做好文件命名。
 - jQuery Validate提供了中文信息提示包，位于下载包的 dist/localization/messages_zh.js，内容如下：

```
(function( factory ) {
    if ( typeof define === "function" && define.amd ) {
        define( ["jquery", "../jquery.validate"], factory );
    } else {
        factory( jQuery );
    }
}(function( $ ) {

/*
 * Translated default messages for the jQuery validation plugin.
 * Locale: ZH (Chinese, 中文 (Zhōngwén), 汉语, 漢語)
 */
$.extend($.validator.messages, {
    required: "这是必填字段",
    remote: "请修正此字段",
    email: "请输入有效的电子邮件地址",
    url: "请输入有效的网址",
    date: "请输入有效的日期",
    dateISO: "请输入有效的日期 (YYYY-MM-DD)",
    number: "请输入有效的数字",
    digits: "只能输入数字",
    creditcard: "请输入有效的信用卡号码",
    equalTo: "你的输入不相同",
    extension: "请输入有效的后缀",
    maxlength: $.validator.format("最多可以输入 {0} 个字符"),
    minlength: $.validator.format("最少要输入 {0} 个字符"),
    rangelength: $.validator.format("请输入长度在 {0} 到 {1} 之间的字符串"),
    range: $.validator.format("请输入范围在 {0} 到 {1} 之间的数值"),
    max: $.validator.format("请输入不大于 {0} 的数值"),
    min: $.validator.format("请输入不小于 {0} 的数值")
});

}));
```

你可以直接复制过去新建文件 messages.js

 - 至此，我们已经将三个插件放入文件夹内了，现在我们来写一份表单的html文件 index.html
 
 index.html

```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>myform</title>
<script>
$.validator.setDefaults({
    submitHandler: function() {
      alert("提交事件!");
    }
});
$().ready(function() {
    $("#commentForm").validate();
});
</script>
<style>
.error{
    color:red;
}
</style>
</head>
<body>
<form class="cmxform" id="commentForm" method="get" action="">
  <fieldset>
    <legend>输入您的名字，邮箱，URL，备注。</legend>
    <p>
      <label for="cname">Name (必需, 最小两个字母)</label>
      <input id="cname" name="name" minlength="2" type="text" required>
    </p>
    <p>
      <label for="cemail">E-Mail (必需)</label>
      <input id="cemail" type="email" name="email" required>
    </p>
    <p>
      <label for="curl">URL (可选)</label>
      <input id="curl" type="url" name="url">
    </p>
    <p>
      <label for="ccomment">备注 (必需)</label>
      <textarea id="ccomment" name="comment" required></textarea>
    </p>
    <p>
      <input class="submit" type="submit" value="Submit">
    </p>
  </fieldset>
</form>
</body>
</html>
```

 - 接下来我们就把三个插件校验引入html文件中，内容如下：

```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>myform</title>
<script src="jquery.js"></script>
<script src="jquery.validate.js"></script>
<script src="messages.js"></script>
<script>
$.validator.setDefaults({
    submitHandler: function() {
      alert("提交事件!");
    }
});
$().ready(function() {
    $("#commentForm").validate();
});
</script>
<style>
.error{
	color:red;
}
</style>
</head>
<body>
<form class="cmxform" id="commentForm" method="get" action="">
  <fieldset>
    <legend>输入您的名字，邮箱，URL，备注。</legend>
    <p>
      <label for="cname">Name (必需, 最小两个字母)</label>
      <input id="cname" name="name" minlength="2" type="text" required>
    </p>
    <p>
      <label for="cemail">E-Mail (必需)</label>
      <input id="cemail" type="email" name="email" required>
    </p>
    <p>
      <label for="curl">URL (可选)</label>
      <input id="curl" type="url" name="url">
    </p>
    <p>
      <label for="ccomment">备注 (必需)</label>
      <textarea id="ccomment" name="comment" required></textarea>
    </p>
    <p>
      <input class="submit" type="submit" value="Submit">
    </p>
  </fieldset>
</form>
</body>
</html>
```





到目前为止，我们完成了一个简单的jQuery Validate 表单验证，

本章工程项目Github的链接：https://github.com/t-wen/jQuery_project


希望我的博客能帮助到大家，感谢阅读我的博客。

---------

