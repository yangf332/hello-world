正则表达式
====================

## 简单模式
* 元字符
  - +,*,\ ([{}]) ^$
* 特殊字符
  - \n, \r, \b ...
* 字符类：用于测试的字符的组合
  - 简单类
    - /[bcf]at/gi
  - 负向类
    - /[^a]/  // 不能匹配
  - 范围类
    - [0-9]
  - 组合类
    - [0-9a-zA-Z]
  - 预定义类
    - \d \D 数字 
    - \s \S 空白
    - \w \W 单词字符
* 量词
  - 简单量词
    - ? * + {n} {n,m} {n,}
  - 贪婪、惰性和支配性量词
    - 贪婪：先看整个字符串，再依次减去最后一个
    - 惰性：先看第一个字符，再读入下一个
    - 支配量词：只匹配整个
    - 简单量词-贪婪；惰性?；支配+

## 复杂模式
* 分组：通过一系列括号包围字符，字符类及量词来使用
* 反向引用（backreference）：存储在分组中的特殊值     
* 候选
  - /(red|black|green)/
* 非捕获性分组
  - 反向引用的分组，称为捕获性分组；非捕获性分组，不会创建反向引用 
  - 左括号后加上一个问号和一个冒号 (?:
* 前瞻
  - 当特定的字符分组出现在另一个字符串之前时，才去捕获它
  - (?=之间)
* 边界
  - ^ & \b 单词边界 \B 非单词边界
* 多行模式
  - //gm
    

### 相关资料


