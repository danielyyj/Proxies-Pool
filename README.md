# Proxies-Pool
实现底层IP代理池存储，上层接口抽象，封装所有对 redis 数据库的操作

代理池三大模块
  代理爬虫模块
  代理测试模块
  代理接口模块
  
  
 脚本实现
代理爬虫程序脚本
#!/usr/bin/env bash
while true
do
    python proxy_spider.py
    sleep 60
done
代理测试程序脚本

#!/usr/bin/env bash

while true
do
    python proxy_tester.py
    sleep 3600
done
代理接口程序脚本

#!/usr/bin/env bash

while true
do
    python proxy_provider.py
    sleep 60
done



##存在问题（未实现）

当代理有问题时就从代理池中移除，但是爬虫程序可能会把有问题的代理重新放回到代理池中导致有问题的代理IP永远移除不了。

解决思路
可以把有问题的代理IP放置到一个黑名单中
当爬虫添加代理时判断代理IP是否存在在黑名单中，如果存在就不添加
在黑名单中的代理IP设置过期时间
