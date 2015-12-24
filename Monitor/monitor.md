| 监控类型 	| 监控内容 	| 监控方法 	| 告警级别 	| 备注 	|
|----------	|----------------------------------------------------------------------------	|----------	|---------------------------------------------------	|------------------------------------	|
| 进程监控 	| redis-server 	| 进程探测 	| 1-正常，0-主要告警 	|  	|            |
| 进程监控 	| redis-sentinel 	| 进程探测 	| 1-正常，0-次要告警 	| 压制两次 	|
| 端口监控 	| 6679 	| telnet 	| 可连接-正常，无法连接-主要告警 	| 与redis-server进程监控二选一即可 	|
| 端口监控 	| 26679 	| telnet 	| 可连接-正常，无法连接-次要告警 	| 与redis-sentinel进程监控二选一即可 	|
| 内存监控 	| redis-cliinfo  Memory &#124; grep used_memory_human &#124; cut -d':' -f2 | sed 's/G//' 	| 数值判断 	| 根据max内存的80%数值为次要告警，90%数值为主要告警 	|  	|
| 日志监控 	| /redis/log/redis-sentinel.log 	| 关键词 	| odown、failover为主要告警 	|  	|