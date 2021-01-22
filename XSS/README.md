# **XSS**

 XSS攻击通常是指通过利用网页开发的漏洞，通过巧妙的注入恶意指令代码到网页，使用户加载并执行攻击者恶意制造的网页程序。
 这些恶意网页程序通常是JavaScript，但实际上也可以包括Java、 VBScript、 LiveScript、ActiveX、 Flash 或者甚至是普通的HTML。攻击成功后，攻击者可能得到包括但不限于更高的权限（如执行一些操作）、私密网页内容、会话和cookie等各种内容。

### **存储型XSS**

   存储型XSS又被成为持久性XSS；它是最危险的一种跨站脚本，相比反射型XSS和DOM型XSS具有更高的隐蔽性，所以危害更大，因为它不需要用户手动触发。允许用户提交和存储数据的web程序都可能存在存储型XSS漏洞，当攻击者提交一段XSS代码后，被服务端接收并存储，当所有浏览者访问这个页 面时都会被XSS；
   其中最典型的例子就是留言本、评论区等功能

    <script>
      while (true) {
          alert('Hello')
      }
    </script>

  这样网站就挂了

    <script>
      alert(document.cookie)
    </script>

  这样可以读取用户的信息

### **DOMXSS**


### **反射型XSS**

