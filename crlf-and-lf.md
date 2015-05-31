CRLF and LF
=============================

### 什么是CRLF和LF
  * CRLF - carriage return line feed，意思是回车换行，相当于"\r\n"
  * LF - line feed 换行

### 不同操作系统的不同处理
  * CRLF -> Windows-style
  * LF   -> Unix Style
  * CR   -> Mac Style

### Git中的转换
  * git config --global core.autocrlf [true|false|input]
  * 参数效果
    - true  : x -> LF -> CRLF
    - false : x -> x -> x  不操作
    - input : x -> LF -> LF (Never windows)
    - x : file to commit -> repository -> checked out file

### 相关链接
  [相关链接](http://itindex.net/detail/49247-crlf-lf?utm_source=tuicool)
  [github](https://help.github.com/articles/dealing-with-line-endings/)
  [stackoverflow](http://stackoverflow.com/questions/1967370/git-replacing-lf-with-crlf)