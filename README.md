## 源码编译：
+ 修改build.properties.default -> build.properties
+ 修改base.path目录为tomcat当前目录下的tomcat-build-libs
+ 执行ant ide-eclipse
+ 执行org.apache.catalina.startup.Bootstrap

## tomcat架构图
![image](https://note.youdao.com/yws/public/resource/11b88babe53bdada374c4355f425bf31/xmlnote/WEBRESOURCEf11612891f2d00e3e779a9318f8bb1c7/7291)

## tomcat启动流程分析
[tomcat启动流程分析](md/StartSequence.md)
+ Bootstrap(main方法) -> Catalina(load方法) -> Catalina(start方法) -> Server(init) 接下来对应的容器的生命周期
+ Server(init) -> LifecycleBase(init -> initInternal) -> StandardServer(initInternal) -> LifecycleMBeanBase(initInternal)
+ StandardServer(initInternal) -> Service(init) -> LifecycleBase(init -> initInternal) -> StandardService(initInternal) -> LifecycleMBeanBase(initInternal) 以下类推


## 源码解析：
+ 运行机制：
```
1、解析server.xml成对应的模块
2、接受客户端连接
3、解析server.xml中的context标签，对应的web application
4、解析web application 中的web.xml，添加servlet
5、servlet处理用户请求
```

+ server.xml模块
```
org.apache.catalina.Server:
org.apache.catalina.Context:
org.apache.catalina.connector.Connector:
```

+ AbstractEndpoint
```
JIoEndpoint
NIoEndpoint
NIo2Endpoint
AprEndpoint
```