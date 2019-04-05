# 1. 安装环境
## 1.1 node.js
node-v9.11 下载链接： 

[点击下载 node-v9.11 x64](https://npm.taobao.org/mirrors/node/v9.11.2/node-v9.11.2-x64.msi)

[点击下载 node-v9.11 x86](https://npm.taobao.org/mirrors/node/v9.11.2/node-v9.11.2-x86.msi)
## 1.2 git
git v2.21.0 下载链接： 

[点击下载 git v2.21.0 32](https://npm.taobao.org/mirrors/git-for-windows/v2.21.0.windows.1/Git-2.21.0-32-bit.exe)

[点击下载 git v2.21.0 64](https://npm.taobao.org/mirrors/git-for-windows/v2.21.0.windows.1/Git-2.21.0-64-bit.exe)

[淘宝镜像](https://github.com/waylau/git-for-win)
## 1.3 编译环境
### 1.3.1 方式一（建议）
以管理员身份打开PowerShell，执行以下命令：

npm i -g windows-build-tools --vs2015

注意：装到一半可能会出现系统更新，如果出现这个情况，等更新完重新运行此命令即可。

### 1.3.2 方式二
python2.7下载链接： 

[点击下载 python2.7](https://npm.taobao.org/mirrors/python/2.7/python-2.7.msi)

[点击下载 python2.7 64](https://npm.taobao.org/mirrors/python/2.7/python-2.7.amd64.msi)

Visual C++ 2015 Build Tools
下载链接： [BuildTools_Full.exe](https://download.microsoft.com/download/5/f/7/5f7acaeb-8363-451f-9425-68a90f98b238/visualcppbuildtools_full.exe)
# 2. ringnetwork超级节点
## 2.1 下载trustnote-pow-supernode
[点击下载 master](https://github.com/trustnote/trustnote-pow-supernode/archive/master.zip)
## 2.2 安装依赖
在trustnote-pow-supernode目录下用命令行运行cnpm install
## 2.3 内网穿透
点击打开免费的内网穿透服务natfrp： [https://www.natfrp.org](https://www.natfrp.org/)，注册账号，
在后台选择“映射列表”，配置如下

| 选项        | 内容    |
| --------  | -----:   |
| 本地地址   | 127.0.0.1      |
|本地端口	|9193|
|远程端口	|点击右下角“随机端口”按钮生成|
|隧道类型	|tcp映射	|
|连接加密	|启用|
|连接压缩	|启用	|

配置完成后，点击“添加”按钮，如提示“错误：此远程端口已经被使用，同一协议（TCP/UDP）单端口只允许使用一次。”则再点击“随机端口”按钮重新生成。
添加成功后，在后台左侧“客户软件”中，下载
windows x86或windows x64客户端，打开后按提示输入账号密码，登录后按需求输入服务器id，建议选国内服务器。
此时会显示“增加代理: [s2.natfrp.org:12345]”的字样，其中，s2.natfrp.org是你的外网url，12345是你之前所生成的外网端口。

## 2.4 修改配置
安装windows版的钱包，生成一个新的钱包，
用编辑器打开超级节点程序目录下的conf.js文件，
修改exports.myUrl = 'ws://10.10.11.50:9193'为exports.myUrl = 'ws://s2.natfrp.org:12345'，这里的s2.natfrp.org改成你之前选的服务器id所对应的url（如果服务器id是10，那就是s10.natfrp.org），12345改成你之前随机生成的远程端口。

将设备地址赋值到exports.safe_device_address：
exports.safe_device_address = "你的设备地址";

将钱包地址赋值到exports.safe_address：
exports.safe_address = "你的钱包地址";

将钱包地址赋值到exports.coinbase_address：
exports.coinbase_address = "你的钱包地址";

## 2.5 运行
在trustnote-pow-supernode目录下用命令行运行node start
## 2.6 创建押金合约
向团队申请测试币，

*****
myURL：'ws://url:port'
SuperNodeAddress：JYGTN8RUDOVP5TQGXRFZJUVIB2NFCFAD
******

领取后，用git bash运行
*****
myURL：'ws://s2.natfrp.org:45043'
SuperNodeAddress：JYGTN7RUDOVP5TQGXRFZJUVIB2NFCFAD
******