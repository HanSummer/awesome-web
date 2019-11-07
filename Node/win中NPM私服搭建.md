``` javascript
一、win 搭建NPM私服：
1. npm install -g verdaccio --unsafe-perm
2. verdaccio : 启动私服，生成配置文件【AppData\Roaming\verdaccio\】
3. 修改配置：config.yaml文件的末尾添加listen: 0.0.0.0:4873
4. verdaccio ：重新启动私服

二、管理npm源 【nrm】
1. npm install -g nrm
2. nrm ls : 查看目前npm有哪些源可以使用
3. nrm add localnpm http://IP:4873 : 手动设置一个IP添加到npm源
4. nrm use localnpm : 切换npm源

三、发布私有包
1. npm adduser：新建一个用户
2. npm login : 登录到私有npm服
3. npm publish ：发布项目包
4. npm unpublish XXX --force ：撤销发布的包

四、npm版本控制：
1. 语义化版本(Semantic versioning)
具体体现为：对于"version":"x.y.z"
1.修复bug,小改动，增加z
2.增加了新特性，但仍能向后兼容，增加y
3.有很大的改动，无法向后兼容,增加x
```
