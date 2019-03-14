## tomcat启动流程
+ 1、命令行启动类：org.apache.catalina.startup.Bootstrap
	+ a、初始化ClassLoader：commonLoader、sharedLoader、catalinaLoader
	+ b、通过catalinaLoader加载org.apache.catalina.startup.Catalina
	+ c、Bootstrap.daemon.init()
+ 2、处理命令行的start、stop参数
	+ a、Catalina.setAwait(true);
	+ b、
		+ b1、initDirs()
		+ b2、initNaming()
		+ b3、createStartDigester()
		+ b4、digester.parse server.xml
		+ b5、initStreams()
		+ b6、init components，包括server标签下的所有组件，调起每个组件的initInternal
	+ c、
		+ 