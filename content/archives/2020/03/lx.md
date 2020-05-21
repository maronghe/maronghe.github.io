项目启动

``````
main.go ->
1.初始化qLog （日志地址、队列大小、并发标识、最小日志级别）
2.init etcd
3. init infra-components ？
4.init project config（cmd -> etcd -> default）
	openHost、appHost、authHost
	app白名单（redirect、cors）
	
	init router -> pathPrefix/api/v1 和 allowOrigin （可信域名）
	init mongo、mysql、redis、crontab、openLog、s3等
	https 需要配置 tls证书和tls私钥 
``````











数据存储

``````
8 bit -> 1 byte (0xab) // 8位 = 1字节
short 16 bit -> 2 byte 
int 32 bite -> 4 byte
int64 64 bite -> 8 byte

``````

