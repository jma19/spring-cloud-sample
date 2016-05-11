#Configuration Server/Client
Spring Cloud提供分布式环境下资源统一配置的功能，用户通过中心的Config Server可以管理整个系统的资源文件，当用户通过Config Server修改配置文件，Config Server会向Config Clients push MQ消息，当Config Client监听到配置修改的MQ消息，相应的更新本地文件。Spring Cloud Config Server使用的数据源默认为Git, 用户可以根据需要自定自己的数据源。


#Config Server
Server对外提供HTTP接口来访问external配置(key value pair或者YAML内容)。使用@EnableConfigServer注解可以很方便的将Config Server集成到Springboot Application中。

##Environment Repository
Config Serevr将configuration data保存在EnvironmentRepository当中，存储多个Environments。 Config Server使用application, profile, label来定位一个Environment资源：

1. application: 对应着client端的"Spring.application.name"
2. profile：对应着client端的"Spring.active.profiles"
3. label：对应着config files的version

###Git Backend
默认的EnvironmentRepository实现使用Git backend，Spring Cloud Config Server支持一个或者多个git repositories。
Config Server默认情况下在第一次配置请求时Clone远端仓储。可以通过cloneOnStart进行配置。



###File System Backend


By default the server clones remote repositories when configuration is first requested. The server can be configured to clone the repositories at startup. For example at the top level:




The default strategy for locating 

/{application}/{profile}[/{label}]
/{application}-{profile}.yml
/{label}/{application}-{profile}.yml
/{application}-{profile}.properties
/{label}/{application}-{profile}.properties