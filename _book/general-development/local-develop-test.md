## 概念阐述

本小节介绍如何在开发者本地进行消费者/提供者应用的开发调试。开发服务提供者请参考3 开发服务提供者章节，开发服务消费者请参考4 开发服务消费者。服务提供者和消费提供者均需要连接到在远程的服务中心，为了本地微服务的开发和调试，本小节介绍了两种搭建本地服务中心的方法进行本地微服务调试：

* 启动[本地服务中心](#section2945986191314)；

* 通过local file模拟启动服务中心\([Mock机制](#section960893593759)\)。

服务中心是微服务框架中的重要组件，用于服务元数据以及服务实例元数据的管理和处理注册、发现。服务中心与微服务提供/消费者的逻辑关系下图所示：  
![](/start/本地开发和测试.png)

## 启动本地服务中心

* **步骤 1 **登录华为公有云[https://servicestage.hwclouds.com](https://servicestage.hwclouds.com/)，选择应用开发-&gt;工具和案例，根据开发的操作系统选择下载对应的本地轻量化服务中心工具。

* **步骤 2 **将下载的localServerCenter-xxx-tar.gz文件解压，window系统下双击运行目录下的start.bat，linux系统下执行start.sh脚本。

window和linux版本均只支持64位系统，linux下执行start.sh脚本前请赋予文件执行权限：

```
　　chmod -R 550 /../bin
```

本地服务中心为提高易用性，默认监听本机地址0.0.0.0的30100端口，但从安全性考虑，建议用户自行修改配置监听127.0.0.1。

* **步骤 3 **启动本地轻量服务中心后，在服务提供/消费者的microservice.yaml文件中配置ServerCenter的地址和端口，示例代码：

```yaml
cse:
 service:
 registry:
 address: 
http://127.0.0.1:30100
 #服务中心地址及端口
```

* **步骤 4 **开发服务提供/消费者，启动微服务进行本地测试。

**----结束**

## Mock机制启动服务中心

* **步骤 1**新建本地服务中心定义文件registry.yaml，内容如下：

```yaml
springmvctest: 
  - id: "001"  
    version: "1.0"  
    appid: myapp #调试的服务id  
    instances:  
      - endpoints:  
        - rest://127.0.0.1:8080
```

#### 注意：mock机制需要自己准备契约，并且当前只支持在本地进行服务消费端\(consumer\)侧的调试，不支持服务提供者\(provider\)

* **步骤 2**在服务消费者Main函数首末添加如下代码：

```java
public class xxxClient {
public static void main(String[] args) {
　　System.setProperty("local.registry.file", "/path/registry.yaml");
    // your code
　　System.clearProperty("local.registry.file");
}
```

setProperty第二个参数填写registry.yaml在磁盘中的系统绝对路径，注意区分在不同系统下使用对应的路径分隔符。

* **步骤 3**开发服务消费者，启动微服务进行本地测试。



