**Message bridge rs 插件安装指南与常见问题解答**

# 简介

通过注册Bot机器人, 实现不同平台用户之间的消息进行同步

以下为Discord与QQ之间平台的相互交流

![](media/c05091a11c84dfcb8d1c0529e2659e45.png)

# 联系方式

本Readme.md 对于新人可能有帮助

本项目forked /rabbitkiller-dev/message_bridge_rs

Discord频道: https://discord.gg/jy3tr4Dq

QQ群：https://jq.qq.com/?_wv=1027&k=D8ymzW7M

欢迎使用和部署, 加入上方联系方式也可以进行体验

# 环境要求与具体部署实施

对于大佬程序员，您只需要浏览以下即可

1\. 科学上网

2\. NodeJs (v14 以上)

3\. 配置config.json文件

部署

1\. Git: 命令: yum install git

2\. NodeJs (v14 以上): 命令启动

3\. 全局安装pm2: npm install -g pm2

4\. Rust + Cargo: 命令: curl https://sh.rustup.rs -sSf \| sh

5\. 配置文件: cp config.simple.json config.json 配置说明: CONFIG.md

命令
```

\> git clone https://github.com/rabbitkiller-dev/message_bridge_rs

\> npm install

\#\# 启动 (pm2进程守护)

\> npm run build

\> pm2 start server.js --name bridge_js

\> pm2 start "cargo run" --name bridge_js
```

对于完全一清二白的小白程序员，请认真读完以下内容，否则出现部署失败

现在假装我们电脑上面什么软件也没有装（以下参考为Windows系统）

1.  安装Github项目克隆器

    你需要首先去下载GitHub克隆器，将我们需要的项目克隆，

    下载地址：[Git - Downloads (git-scm.com)](https://git-scm.com/downloads)

    下载完成后你会获得一个安装包，打开后一路Next即可，最后会显示安装成功

    现在在桌面上或者你想要的位置新建一个文件夹，然后在这个位置打开命令

    ![](media/e36396d91771927587e25b307dea275e.png)

    输入
    ```

    Git clone <https://github.com/rabbitkiller-dev/message_bridge_rs.git>
    ```

    这样你会在这个文件夹得到一个新的子文件夹

    如果提示下载失败，建议直接在网站下载

    ![](media/7c7c427813ffc2ccbfe8876d543dd0e6.png)将东西解包出来然后直接往你需要的文件夹里面一拖就行了

    ![](media/1873341e574fa7e02cfce6c002984826.png)

    打开该文件夹，这里便是这个程序的根目录了

    ![](media/16e9dd3945fa203524a9e8c753ce98e3.png)

2.  安装NodeJs

    这里下载NodeJs，这个程序将支持我们程序的后台运行

    [Download \| Node.js (nodejs.org)](https://nodejs.org/en/download)

    照样，一路Next就行了

    到这一步的时候，十分建议将这个勾选

    ![](media/844bcf9ed6f26da27329b5f784303b43.png)

    之后坐等安装完成即可

3.  安装全局PM2

    现在，在这个位置（以下称为“根目录”）打开命令

    ![](media/16e9dd3945fa203524a9e8c753ce98e3.png)

    输入
    ```
    npm install -g pm2
    ```

    ![](media/a22c315982f3bd165194457041d4c205.png)

    ![](media/911c2d61eac6091244647e87ae3840ac.png)

    到这步，PM2就安装完成了

4.  安装Rust与Cargo

    这里下载Rust，这个程序将支持我们程序的启动

    [Install Rust - Rust Programming Language (rust-lang.org)](https://www.rust-lang.org/tools/install)

    安装器打开后会得到这个界面

    ![](media/c3f6246a6afc639f425f70ae3fa39d29.png)

    如果嫌麻烦，选择3然后1就行，但建议在这个界面直接选择1

    等安装完毕即可

    ![](media/ccd4c2ace5a171ba5c4719cbba9d7f02.png)

    出现如上所示便完成安装了

    现在打开之前预留在后台的命令框，输入
    ```
    rustup default nightly
    ```

    检查是否安装成功，出现这个框说明是正常的

    ![](media/394e30a9f9c12956da112569d833fbef.png)

5.  Discord机器人搭建

    既然需要实现Discord与QQ互通，就需要一个Discord机器人，打开这个网址（注意，你需要科（fan）学（qiang）上网）

    [Discord Developer Portal — My Applications](https://discord.com/developers/applications)

    获得如下界面

    点击New application创建一个新的机器人

    ![](media/4e6d9c90d9082d3383e2484a9132be88.png)

    名字随便取，你喜欢的就行

    ![](media/004095dbbb8d64edb0cb44918885b070.png)

    ![](media/cddc7669d93a42cab7462fca629c2795.png)

    ![](media/a98770efd4c2bace8cdb406a3c31a4c3.png)

    ![](media/f41329c249e467f4d418e6b4782ba333.png)

    ![](media/a7843f0e6cf9ebb6acc7145bfc4dc461.png)

    ![](media/a24dc124b9318e3c6fe478f79eb6f904.png)

    ![](media/0cd9ef15d4e3848ffc07e38cdc2fcf0c.png)

    复制如下的网址
    ```
    https://discord.com/oauth2/authorize?client_id=client_id&scope=bot&permissions=permissions
    ```

    修改一下连接的client_id和permissions参数：

    将标红的位置改成你刚刚保存的数字

    然后打开网址，会提示邀请至频道，选择你需要邀请的Discord服务器（这个频道最好是你主管），将机器人邀请进来

    现在打开Discord，打开机器人邀请进来的Discord服务器，进入

    ![](media/145359129135d11cbd2521391aafbfce.png)

    保存服务器ID，WebHook以及token

    ![](media/2e2f7791824f9838fcd6f8263aa82cfe.png)

    ![](media/69dfdc375b1bfe7487005429996caf19.png)

    ![](media/0d9c19b383fc2ba7fc89ab76181c5e32.png)

    ![](media/78b45ed903023d75d9c15eb054090410.png)

    ![](media/d87715770ebcc8f03687f710a227bc60.png)

6.  配置Config.json

    现在回到我们的程序根目录，我们在文件夹给了一个叫做config.sample.json，打开这个文件，就会有说明

    其中

    ![](media/96d2331d5dad926f6510d9f0cb4e30fb.png)

    QQ方面
    ```
    BotID：你需要作为机器人的QQ账号

    Password：QQ密码

    Version：上图任意选一个就行

    Auth：两者选其一，QR（二维码）会更快一点
    ```
    ```
    Discord方面

    BotID：将之前保存下来的机器人ID复制到这个位置

    Token：将之前生成的机器人Token复制到这个位置
    ```

    Bridge方面

    Discord项目：
    ```
    Id：将之前浏览器复制Webhook的id放到这个位置

    Token：将之前浏览器复制Webhook的Token放到这个位置

    ChannelID：将之前浏览器复制Webhook的Channelid放到这个位置
    ```
    QQ项目：
    ```
    QQGroup：把你需要消息互通的QQ群的群号放到这个位置（这个QQ群必须有你的机器人）
    ```

    以下为示例

    ![](media/6db5674fa901712019d925ed60060309.png)

保存，将这个文件的文件名修改为config.json，一定要改，不然等会程序无法运行

1.  运行部署程序

程序根目录打开命令

输入命令
```
npm install
```
完成后输入
```
npm run build
```
![](media/6d90d070d5a845e1bcfe8f9a77ba993f.png)

得到这个界面后便完成了程序初步安装

开始架设交互桥，输入命令
```
pm2 start server.js --name bridge_js
```
![](media/c70dd0eca9d376776d6396a3e29e44a8.png)

得到这个界面，现在输入
```
Cargo run
```
开始交流沟通

![](media/803d1deb76053e8ba08640697117126a.png)

登录QQ，成功后便显示成这样了

![](media/0eb5b7932543d383efeb84746b8044af.png)

至此，恭喜，你完成了搭建，现在享受互通聊天吧。

之后每次重新启动软件，输入cargo run即可

重启电脑后，需要输入
```
\> npm run build

\> pm2 start server.js --name bridge_js

然后再cargo run即可
```
## 常见问题
1.  输入cargo run后提示未链接到主机，或者积极拒绝链接等？

    答：最好换一个科学上网的软件

2.  输入cargo run后，启动程序，提示

    run:recv_event:handle_event:handle+gateway+closed然后自动退出Discord？

    答：这种情况十有八九是Discord机器人配置出问题了，重新配置Discord机器人然后重写config.json

3.  程序启动后，一直提示“由于连接方…尝试连接失败”？

    答：同 问题2

4.  Nodejs提示端口被占用？

    答：直接随便在某处打开命令，然后输入

    node server.js

    查看是否被占用

    若被占用（一般占用的端口号为3000），输入

    netstat -aon\|findstr "3000"

    之后查看哪个软件占用了这个端口，在任务管理器关闭这个软件就行了

    最后按照默认步骤
```
    \> npm run build

    \> pm2 start server.js --name bridge_js
```
    然后再cargo run即可
