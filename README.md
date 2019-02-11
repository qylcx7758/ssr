# ssr
## 怕相关网站和资源被墙，做的备份，大多是搬运和少部分自己的经验；
## 参考的网站（下面网站2019年2月11日均可用）

[vultr中文网](https://www.vultrcn.com/)

[青蛙君手机ssr教学](http://www.frogjun.com/fq-a/)

[Vultr五分钟快速搭建SS科学上网从vps到SSR详细干货教程](https://segmentfault.com/a/1190000015899470)


### 一、vultr网站购买服务器
1. 进入网站[https://www.vultr.com/](https://www.vultr.com/)注册登录；

2. 进入购买服务器（新手建议可以先不买热门的服务器，例如日本，洛杉矶的，经常被封Ip,端口，然后要换好多次服务器才行）

 ![](https://user-gold-cdn.xitu.io/2019/2/11/168dba2fc9085414?w=1307&h=417&f=png&s=90034)

![](https://user-gold-cdn.xitu.io/2019/2/11/168dba412d387e09?w=926&h=541&f=png&s=91168)
  
  ![](https://user-gold-cdn.xitu.io/2019/2/11/168dba5fb19d8ea2?w=855&h=529&f=png&s=117889)

3. 自行支付宝充值付账，vultr的服务器它是按照时间计费的（（2019.02.11）新账号用paypal支付有优惠，但我是支付宝，网上也有一些优惠码，自行搜索；）；

4. 这就是你的服务器

 ![](https://user-gold-cdn.xitu.io/2019/2/11/168dbaa34b5f1d47?w=868&h=383&f=png&s=50784)

### 二、Xshell连接服务器
#### 1. 文章主要讲述整体流程，其他不多赘述，自行下载Xshell

#### 2. 新增服务器连接
![](https://user-gold-cdn.xitu.io/2019/2/11/168dbac4c3e40730?w=616&h=303&f=png&s=31853)

- 输入需要连接的服务器地址
![](https://user-gold-cdn.xitu.io/2019/2/11/168dbae73012fbcc?w=542&h=454&f=png&s=38410)

- 输入密码
![](https://user-gold-cdn.xitu.io/2019/2/11/168dbb11f8e62496?w=586&h=486&f=png&s=47060)

#### 3. 点 文件>打开，选中会话，进行连接

![](https://user-gold-cdn.xitu.io/2019/2/11/168dbb61e3e5a410?w=688&h=611&f=png&s=93148)

#### 4. 如果该ip和22端口没有封，则如图

![](https://user-gold-cdn.xitu.io/2019/2/11/168dbb6d6ab214e4?w=633&h=260&f=png&s=21650)
Tip: 
- （1）建议购买服务器后，先尝试Ping该服务器Ip，看国内是否被封；
- （2）tcping （一个ping端口的工具，需要下载）该Ip和22端口,例如
`tcping  149.28.158.234 22`，如果被封，则ssh无法连接；
- （3）[测试端口是否开放](http://coolaf.com/tool/port)，如果关闭，直接更换新的服务器；
- （4）[ping各地网速](http://ping.chinaz.com/45.32.79.9)；

### 三、连接成功后，搭建ssr（以下多为粘贴，用作备份）
#### 1. 复制下面代码，回车运行
中文版：
```shell
wget --no-check-certificate -O shadowsocks-libev_CN.sh https://raw.githubusercontent.com/uxh/shadowsocks_bash/master/shadowsocks-libev_CN.sh && bash shadowsocks-libev_CN.sh

```
英文版：（如果中文版执行后出现乱码，那么请使用这个）
```shell
wget --no-check-certificate -O shadowsocks-libev.sh https://raw.githubusercontent.com/uxh/shadowsocks_bash/master/shadowsocks-libev.sh && bash shadowsocks-libev.sh
```
如图
![](https://user-gold-cdn.xitu.io/2019/2/11/168dbcda5034d0c7?w=800&h=96&f=png&s=54586)

#### 2.

 ![](https://user-gold-cdn.xitu.io/2019/2/11/168dbce248f881b4?w=380&h=268&f=png&s=84480)
#### 3. 加密方式我的实践和网上的一些说法，推荐（6）chacha20，别用默认的，7我也成功过；

![](https://user-gold-cdn.xitu.io/2019/2/11/168dbcede389c6e1?w=800&h=428&f=png&s=257683)

#### 4. 大约 2~5 分钟即可安装完成，完成后保存SS信息，就能使用了（cat 此文件可看配置信息）;

![](https://user-gold-cdn.xitu.io/2019/2/11/168dbd0c9b4d9b88?w=800&h=151&f=png&s=135237)

### 四、下载小飞机，通过粘贴ssr链接或者手动输入IP、端口、密码等配置信息编辑服务器，选择服务器后，选择pac或者全局代理（自行下载）；

![](https://user-gold-cdn.xitu.io/2019/2/11/168dbd3eb1b73a7c?w=619&h=405&f=png&s=44731)


- 当通过小飞机可以谷歌的时候（如果有设置多个可用服务器，建议多搜索一些东西，稍微多点进去一些网站，因为类似缓存的机制，可能是因为原先设置的代理服务器造成的暂时可以谷歌搜索，实际上很多网站依旧进不去）

### 五、安装锐速来加速（如果觉得网速慢了，可以考虑安装锐速来加速，以下多为粘贴，用作备份）

#### 1. 回到Xshell，输入以下命令；

```shell
uname -r
```

回车后输出当前系统内核版本。主要分三种情况,选择一种安装锐速：

（1）结果以 2 开头，例如 2.6.32-696.18.7.el6.x86_64。

这种输出结果说明我们的服务器为 CentOS6 x64 系统，大家直接查看第三步进行锐速安装即可。

（2）结果以 3 开头，例如 3.10.0-693.11.6.el7.x86_64。

这种输出结果说明我们的服务器为 CentOS7 x64 系统，大家直接查看第四步进行锐速安装即可。

（3）结果以 4 开头，例如 4.12.10-1.el7.elrepo.x86_64。

这种输出结果说明我们的服务器已经安装 Google BBR 拥塞控制算法，此时已经无法继续安装锐速。

#### 2. CentOS6 x64 系统安装锐速
若第二步中确定服务器为 CentOS6 x64 系统则看这一步。

按照下图提示，我们继续复制下列命令：
```shell
wget --no-check-certificate -O appex.sh https://raw.githubusercontent.com/0oVicero0/serverSpeeder_Install/master/appex.sh && bash appex.sh install '2.6.32-642.el6.x86_64'
```
然后回到 Xshell 软件，鼠标右键选择粘贴，回车继续。然后一直回车就行，成功有提示的；


#### 3. CentOS7 x64 系统安装锐速
若第二步中确定服务器为 CentOS7 x64 系统则看这一步。

按照下图提示，我们继续复制下列命令：

```shell
wget --no-check-certificate -O rskernel.sh https://raw.githubusercontent.com/uxh/shadowsocks_bash/master/rskernel.sh && bash rskernel.sh
```
然后回到 Xshell 软件，鼠标右键选择粘贴，回车继续。


回车后系统会自动下载脚本并执行更换内核命令，等待内核更换完毕后系统会自动重启并断开连接。


系统重启后，Xshell 软件会断开连接。等待 3~5 分钟服务器即可重启完毕，我们重新连接服务器，按照下图提示，我们继续复制命令：

```shell
yum install net-tools -y && wget --no-check-certificate -O appex.sh https://raw.githubusercontent.com/0oVicero0/serverSpeeder_Install/master/appex.sh && bash appex.sh install
```

然后回到 Xshell 软件，鼠标右键选择粘贴，回车继续。


设置完三项信息完成后，系统会完成锐速安装并输出锐速的运行状态。

#### 4.按照下图提示，当出现红框内信息时说明锐速已完成安装并开机自启动。
![](https://user-gold-cdn.xitu.io/2019/2/11/168dbe7b63ae5b32?w=448&h=155&f=png&s=22845)
