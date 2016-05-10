#Configuration Server/Client
Spring Cloud提供分布式环境下资源统一配置的功能，用户通过中心的Config Server可以管理整个系统的资源文件，当用户通过Config Server修改配置文件，Config Server会向Config Clients push MQ消息，当Config Client监听到配置修改的MQ消息，相应的更新本地文件。Spring Cloud Config Server使用的数据源默认为Git, 用户可以根据需要自定自己的数据源。


##Config Server
Server对外提供HTTP接口来访问external配置(key value pair或者YAML内容)。使用@EnableConfigServer注解可以很方便的将Config Server集成到Springboot Application中。





The default strategy for locating 

/{application}/{profile}[/{label}]
/{application}-{profile}.yml
/{label}/{application}-{profile}.yml
/{application}-{profile}.properties
/{label}/{application}-{profile}.properties