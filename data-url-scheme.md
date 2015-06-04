Data URL scheme
=============================

### 格式
    data:[<mediatype>][;base64],<data>
    
### 目前支持类型
    data:,<文本数据>
    data:text/plain,<文本数据>
    data:text/html,<HTML代码>
    data:text/html;base64,<base64编码的HTML代码>
    data:text/css,<CSS代码>
    data:text/css;base64,<base64编码的CSS代码>
    data:text/javascript,<Javascript代码>
    data:text/javascript;base64,<base64编码的Javascript代码>
    data:image/gif;base64,base64编码的gif图片数据
    data:image/png;base64,base64编码的png图片数据
    data:image/jpeg;base64,base64编码的jpeg图片数据
    data:image/x-icon;base64,base64编码的icon图片数据

### 优点
* 页面中节省HTTP请求

### 缺点
* 浏览器无法做缓存
* 做base64编码后长度增加1/3左右

### 代码
* 将编码转为文件

    ```
    /// php
    if (preg_match('/^(data:\s*image\/(\w+);base64,)/', $img_content, $result)){
      $type = $result[2];
      $new_file = "./test.{$type}";
      if (file_put_contents($new_file, base64_decode(str_replace($result[1], '', $img_content)))){
        echo '新文件保存成功：', $new_file;
      }
    }
    ```

### 相关链接
  [rfc](http://www.ietf.org/rfc/rfc2397.txt)