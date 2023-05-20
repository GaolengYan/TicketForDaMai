### python环境
* python3.6.3
  * 建议安装我推荐的这个版本，其他版本或多或少存在点问题
  
### 包下载
* 推荐使用清华源或者豆瓣源下载
  * pip install -i https://pypi.tuna.tsinghua.edu.cn/simple requests selenium==4.2.0 lxml
  * pip install requests selenium==4.2.0 lxml -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com


### chromedriver配置
* 载完chrome浏览器之后，点击浏览器最右边的三个点，依次点击---》帮助---》关于Google Chrome，查看自己的Chrome版本

  <img src="https://img-blog.csdnimg.cn/26ac31256b5a4049a68b52991fe0b3f7.png#pic_center" alt="在这里插入图片描述" style="zoom:50%;" />

* 下载和Chrome版本对应的ChromeDriver软件 

  * 链接：http://chromedriver.storage.googleapis.com/index.html 

  * 我自己的Chrome版本是110.5481.78，那么就在链接里找到对应chromedriver的版本，并进行下载，这里我下载的是**windows系统**

    可以看到，链接中并没有完全一致的版本，那么就**挑选一个和当前chrome版本日期最近的版本**，因此这里我选择下载104.0.5112.79

    <img src="https://img-blog.csdnimg.cn/631b602ffebe4e1693a12f5caf94d64e.png#pic_center" alt="在这里插入图片描述" style="zoom:67%;" />

    点进去，继续下载

    <img src="https://img-blog.csdnimg.cn/a7a674a4b47746298f3f236bb66a8caa.png#pic_center" alt="在这里插入图片描述" style="zoom: 67%;" />

​              windows系统下载win32位的zip压缩包即可

* 下载之后进行解压，得到**chromedriver.exe**

  * 打开安装chrome浏览器的目录，将 **chromedriver.exe**放入当前目录中

  <img src="https://img-blog.csdnimg.cn/c29caa0656ef4ab190cc96387a63f61b.png#pic_center" alt="在这里插入图片描述" style="zoom:67%;" />

### 参数设置

在`config.json`中输入相应配置信息，具体说明如下：

* `date`: 日期选择
* `sess`: 场次优先级列表，如本例中共有三个场次，根据下表，则优先选择1，再选择2，最后选择3；也可以仅设置1个。
* `price`: 票价优先级，如本例中共有三档票价，根据下表，则优先选择1，再选择3；也可以仅设置1个。
* `real_name`: [1,2], 实名者序号，如本例中根据序号共选择两位实名者，根据序号，也可仅选择一位
  * 选择一位或是多位根据购票需知要求，
  * 若无需实名制信息则不需要填写，
  * 若一个订单仅需提供一位购票人信息则选择一位，
 * 若一张门票对应一位购票人信息则选择多位）。
 
* `nick_name`: 用户在大麦网的昵称，用于验证登录是否成功
* `ticket_num`: 购买票数
* `damai_url`: https://www.damai.cn, 大麦网官网网址
* `target_url`: https://detail.damai.cn/item.htm?id=599834886497  目标购票网址

* 部分门票需要选择城市，只需选择相应城市后将其网址复制到config.json文件的target_url参数即可。

* 根据需要选择的场次和票价分别修改config.json文件中的sess和price参数。

* 查看购票须知中实名制一栏，若无需实名制则config.json文件中的real_name参数不需要填写（即为[]）；若每笔订单只需一个证件号则real_name参数只需选择一个；若每张门票需要一个证件号，则real_name参数根据需购票数量进行相应添加。


* 若是首次登录，根据终端输出的提示，依次点击登录、扫码登录，代码将自动保存cookie文件（cookie.pkl）

* 使用前请将待抢票者的姓名、手机、地址设为默认。

* 配置完成后执行python damai_ticket.py即可,注意观察控制台输出。

* 本代码为保证抢票顺利，设置循环直到抢票成功才退出循环，若中途需要退出程序请直接终止程序。

### 答疑
* selenium版本
   * 4.2.0再往上就有问题了
* Github上的源码是否为最新代码
  * 不是最新代码，滑块过不了
* 出现网络拥堵
  * 没有过滑块
* 是否支持选座
  * 不支持
