Charset
====================


### 字符集

* ASCII（American Standard Code for Information Interchange，美国标准信息交换代码）
  - 它是现今最通用的单字节编码系统，并等同于国际标准ISO/IEC 646

* Unicode
  - Unicode是国际组织制定的可以容纳世界上所有文字和符号的字符编码方案
  - Unicode用数字0-0xFFFF来映射这些字符，最多可以容纳65536个字符，或者说有65536个码位。码位就是可以分配给字符的数字
  - **Unicode的实现方式称为Unicode转换格式（Unicode Transformation Format，简称为UTF）**
  - UTF-8、UTF-16、UTF-32都是将数字转换到程序数据的编码方案

* UTF-8
  - UTF-8（8-bit Unicode Transformation Format）是一种针对Unicode的可变长度字符编码
  - 由Ken Thompson于1992年创建。现在已经标准化为RFC 3629
  - UTF-8用1到6个字节编码UNICODE字符。
* CJK 中日韩统一表意文字
  - 目的是要把分别来自中文、日文、韩文、越南文、壮文中，起源相同、本义相同、形状一样或稍异的表意文字，赋予其在UISO 10646及万国码标准中相同编码

* GBK即汉字内码扩展规范（Chinese Internal Code Specification）

* 摩尔斯电码（英语：Morse Code）
  - 是一种时通时断的信号代码，通过不同的排列顺序来表达不同的英文字母、数字和标点符号。是由美国人萨缪尔·摩尔斯在1836年发明。

### 相关资料

[bootless](http://tadaland.com/os-x-rootless.html/)


