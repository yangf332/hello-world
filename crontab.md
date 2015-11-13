crontab
=============

#### crontab定时任务
    通过crontab 命令，我们可以在固定的间隔时间执行指定的系统指令或 shell script脚本。时间间隔的单位可以是分钟、小时、日、月、周及以上的任意组合。这个命令非常适合周期性的日志分析或数据备份等工作。

#### 命令格式
    crontab [-u user][-e | -l |-r]

#### 命令参数
* -u user
* -e 编辑文件内容
* -l 显示文件内容
* -r 删除
* -i 删除时提示确认

#### 文件格式
* 分 时 日 月 星期 要运行的命令
* 第1列分钟1～59
* 第2列小时1～23（0表示子夜）
* 第3列日1～31
* 第4列月1～12
* 第5列星期0～6（0表示星期天）
* 第6列要运行的命令

#### 例子
    * * * * * myCommand   // 每1分钟执行一次 
    * */1 * * * myCommand   // 每小时
    3,15 * * * * myCommand  // 每小时的第3和第15分钟执行
    3,15 8-11 * * * myCommand  // 在上午8点到11点的第3和第15分钟执行
    3,15 8-11 */2  *  * myCommand  // 每隔两天的上午8点到11点的第3和第15分钟执行
    3,15 8-11 * * 1 myCommand  // 每周一上午8点到11点的第3和第15分钟执行
    30 21 * * * myCommand  // 每晚的21:30

#### 一个例子
      - #SP_BIN_PHP="/usr/local/php"
      - #SP_LOGS_PATH="/usr/logs/"
      - /* * * * * $SP_BIN_PHP  test.php >> $SP_LOGS_PATH/test.log 2>&1

#### FAQ
* 有时我们创建了一个crontab，但是这个任务却无法自动执行，而手动执行这个任务却没有问题，这种情况一般是由于在crontab文件中没有配置环境变量引起的。



#### 备份
    crontab -l > $HOME/mycron


### 相关链接
* [crontab](http://linuxtools-rst.readthedocs.org/zh_CN/latest/tool/crontab.html)
 