# 用途
为数据买卖双方提供端-端的交付。

更多信息，查看: https://www.datoms.cn/datube.html

## 使用方法

Git clone 镜像: https://github.com/ox1bdat/sc-base

数据卖方，采取如下步骤交付数据：
1. 启动管道服务  
   `docker run -d -p 3000:3000 semcon/sc-base`
2. 初始化服务  
   `curl -H "Content-Type: application/json" -d "$(< init.json)" -X POST http://localhost:3000/api/desc`
3. 写入数据  
   `curl -H "Content-Type: application/json" -d '{"my": "data"}' -X POST http://localhost:3000/api/data`
4. 读取或检查数据  
   `curl http://localhost:3000/api/data`
5. 提交数据交付管道  
   `docker commit container_name semcon/data-example`  
   `docker commit container_name semcon/data-example`
   
数据买方，采取如下步骤获取数据：
1. 启动管道服务
2. 读取数据
`docker run -d -p 3001:3000 semcon/data-example`  
   `curl http://localhost:3001/api/data`
