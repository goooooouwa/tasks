# 云主机 & Eclipse Che

## 用途：

1. 架设[Eclipse Che](https://www.eclipse.org/che/)云IDE开发环境，免去零基础同学搭建开发环境的烦恼。
2. 方便助教做代码审查，及时给出反馈。
3. 以后把自己的项目直接架设在云主机上。



## 购买方法：

[【京东云学生机思特沃克学院优惠购买链接】](http://www.jcloud.com/productTrialforPay?uuid=96078dc1-e1a8-4091-a4e1-d8f0a3a8ad1d)


- 价格：10元可使用3个月
- 配置：1C2G1M，华北，每人限购1台，需要在线通过学生认证。
- 注意：优惠数量有限，链接无法识别是否为思沃学员，因此请同学们不要外传。

【学生认证方式】

- 本科生：在活动官网在线认证即可。如有问题可查看帮助文档：http://www.jcloud.com/help/detail/1346/isCateLog/1 ，以及活动主页的说明：http://www.jcloud.com/activity/leapCloud

- 研究生：研究生在线认证尚未开通，需要提供以下信息（https://jinshuju.net/f/ltmGFD）：

  1. 学生姓名
  2. 学校
  3. 专业
  4. 手机号
  5. 手持包含身份证件的照片。

  - 照片要求：本人正面照，同时手持学生证或校园一卡通，露出包含学生身份的关键页（露出姓名、学校公章、日期等信息）
  - 研究生已经向助教提交的可以不用通过金数据提交



## 京东云 创建实例教程

1. 登录京东云账号

2. 点击[创建云主机的链接](http://www.jcloud.com/productTrialforPay?uuid=96078dc1-e1a8-4091-a4e1-d8f0a3a8ad1d)，创建主机

   - 选择官方镜像 ubuntu 16.04 64位

     ![](http://upload-images.jianshu.io/upload_images/6971659-f3971492dd7b9430.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   - VPC选择默认选项就行，其他都不用设置

     ![](http://upload-images.jianshu.io/upload_images/6971659-f38861b0d74d8095.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   ​

   立即购买就行了

3. 接下来进入控制台界面

   - 登云主机创建好以后，先停止云主机	![](http://upload-images.jianshu.io/upload_images/6971659-4b5c7096f328adc2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

     ![](http://upload-images.jianshu.io/upload_images/6971659-6704a3defe523f3f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   - 停止以后，在更多菜单中选择重置系统，

     ![](http://upload-images.jianshu.io/upload_images/6971659-a7dfedf4c8dfc5d1.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   - 点击更换镜像，镜像类型为共享，选择共享镜像**（需要找自己的助教共享）**为tws-eclipse-che-v1 Ubuntu 16.04，如上图所示。

   - 密码自己设置自己的密码，记住就行，然后点击确定。然后会提示是否重置，确定就行。

   - 然后就是等待系统重置完成。系统重置完成之后是停止状态，再启动就行了。

4. 云主机实例创建完成。

5. 查看自己的公网IP地址

   ![](http://upload-images.jianshu.io/upload_images/6971659-4b5c7096f328adc2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




## 修改CHE配置

我们需要按照如下步骤连接到自己的服务器修改`che.env`文件，将里面的IP地址设为自己服务器的公网IP地址。

### 预备工作

- **下载并安装Xshell**（一款远程连接服务器进行管理的软件，MAC下可使用自带的SSH）·[教程](http://jingyan.baidu.com/article/295430f13fb4db0c7f005065.html)

- **查看自己京东云主机公网IP**

### 修改配置文件

- 首先我们需要连接到自己的服务器

  - 若为Windows，安装`Xshell`并打开，选择`新建站点`，输入服务器的公网IP并连接，并在弹出的提示框中输入账号密码，默认会进入自己的服务器`~`目录

    ![](http://upload-images.jianshu.io/upload_images/6971659-815238c7c959c2cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    ​

  - 若为MAC 或 Linux系统，则在`Terminal`里输入

    `ssh root@111.222.333.444`**（其中111.222.333.444为自己的公网IP）**

    **即可登陆自己的服务器，也会默认进入服务器的`~`目录，如下**

    ![tws-che-init](http://otbwgn2nv.bkt.clouddn.com/57f1ffd5c2918be6fb3a84306f49c166.png)

  **下列步骤各种系统的操作一样**

- 从登入服务器的`~`目录进入配置文件所在目录，输入命令

    `cd EclipseChe`进入EclipseChe目录

    `ls -l`列出目录下文件

    可以看到如下输出

    ![tws-che-init](http://otbwgn2nv.bkt.clouddn.com/a1f31f7b2cc39edc6e65978091371fba.png)

    其中`che.env`是我们需要修改的文件，`init-che.sh`是我们用到的修改脚本

- 输入`./init-che.sh`运行脚本，会被问及自己的公网IP，输入自己的公网IP后回车

  ![tws-che-init](http://otbwgn2nv.bkt.clouddn.com/70ff534596a2ed576b1476e6605b6766.png)

  静静的等待`che`重启成功，大概五分钟左右

## 添加workspace

第二步我们需要添加自己的workspace，打开浏览器，输入自己的公网`IP地址:8080`访问`che`的管理界面,例如`111.222.333.444:8080`

- 在左边的菜单栏选择`WorkSpaces`
- 单击`Add WorkSpace`
- 在`SELECT STACK`下，将滚动条拉到最下面选择本次训练营主要用到的`tws-node-7`这一个环境

  ![](http://upload-images.jianshu.io/upload_images/6971659-41ff7d160982558e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 单击网页下侧的绿色按钮`CREATE`完成配置

然后选择左侧的新建的workspace就可以开始体验在线编程环境了，恭喜你！
