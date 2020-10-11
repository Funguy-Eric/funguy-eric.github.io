## HTML
### HTML-表单标签
1. form标签
属于同一个表单的表单控件要包含在同一个块状元素`<form>`里
form的两个属性，`action`and `method`:
  * `action`: 一个处理此表单信息的程序所在的 URL，所述表格信息将在表单提交时被发送到定义的地址。

  * `method`: 它的值可以是 GET 或 POST，用来规定 如何 发送表单信息。
    
    <!-- <form>是块状标签，要注意：<form>标签不能嵌套<form>标签 -->

 `<form action="">`
  <!-- 这里会有一些表单控件 -->
  `</form>`

2. input: 单行文本输入框

```html
  <input type="text" placeholder="hello" name="one" value="Hi" readonly />
```

> placeholder: 占位文本，用来提示用户需要输入什么
name: 输入框名称，用于区分于其它输入框
value: 输入框的预填值
readonly/disabled: 前者仅表示输入框内容不可修改，后者还使该值不会被提交  

other type:
  * `password`: 密码框
  * `radio`: 单选框
  * `checkbox`: 复选框

3. textarea: 多行文本输入框

   当多行文本输入框中输入的内容超过一行的长度时，它会自动换行，而单行文本输入框则不会换行。

   ```html
   <!-- name属性表示表单元素的名称，placeholder属性表示表单元素的占位文本 -->
   <textarea
     name="sign"
     rows="5"
     cols="30"
     placeholder="请输入个性签名"
   ></textarea>
   ```

   > rows：行数
   >
   > cols：文本框的可视宽度

   

4. 选项菜单

   ```html
   <select name="career">
     <option value="default">请选择你的英雄</option>
     <option value="staff">亚瑟</option>
     <option value="freelancer">赵云</option>
     <option value="student">露娜</option>
     <option value="other">马超</option>
   </select>
   ```

   > 给`select`加上multiple属性后，按住`ctrl`即可多选

   
   
5. 按钮标签

   ```html
   <button type="submit">注册</button>
   ```

   type="submit"属性确保数据的提交

### HTML5-语义化标签

* 常用的语义化标签

        1.  `<header></header>`常用来表示网页的顶部
           2.  `<main></main>`常用来表示网页的主体内容区域
           3.  `<nav></nav>`常用来表示导航栏一类
           4.  `<aside></aside>`常用来表示侧边栏
           5.  `<section></section>`类似__<div>__，表示区域
           6.  `<footer></footer>`常用来表示网页底部，比如相关链接，copyright等