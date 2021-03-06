#  **PConnect 全栈必备** 
PConnect是基于AngularX+SpringCloud的企业级基础功能框架(户权限管理、菜单管理、组织管理、知识库管理、......)，其核心设计目标是提供大型项目框架模版直接开发、快速开发、学习简单、功能强大、不重复造轮子

交流QQ群：23592723 

主要技术：

- 前端技术：AngularX；
- 后端技术：SpringCloud；
 

# 架构设计 

### 架构原理图

![img](http://on-img.com/chart_image/5954b886e4b0ad619ac73246.png)

### 对单机项目的整合

当我在想用一个什么项目作为老项目的时候，找我的收藏夹，发现了一个不错的开源项目（若依RuoYi），在这里他表示感谢！
所以我打算找多个“老项目”进行整合，也作为一个示范，RuoYi是第一个

对“老项目”的整合采用“绞窄模式(Strangulation Patterns)”(见[Martin Fowler的博客](https://martinfowler.com/bliki/StranglerApplication.html))进行，放在strangulation目录下。这些“老项目”自身的说明，请见对应项目目录。

##### 整合一：
* RuoYi


## 前端技术：Angular；
支持angular2、4、5版本，UI使用[AdminLTE](https://github.com/almasaeed2010/AdminLTE)；
- angular-cli
- TypeScript
- 组件
- 模板 
- 模块
- 服务
- 依赖注入
- 动态路由 
- Http


## 后端技术：SpringCloud；
- Eureka  
    服务器用作服务注册服务器。
    一个java客户端，用来简化与服务器的交互、作为轮询负载均衡器，并提供服务的故障切换支持。
- Zuul  
    基于JVM路由和服务端的负载均衡器
    类似nginx，反向代理的功能
- Hystrix  
    提供了熔断、隔离、Fallback、cache、监控等功能，能够在一个、或多个依赖同时出现问题时保证系统依然可用。
- Feign  
    是声明式、模板化的http客户端。旨在用最少的开销和代码将您的代码连接到http apis。
- Ribbon  
    提供客户端的软件负载均衡算法
- Redis  
    存储热点数据
- Session
    redis存储热点、共享会话数据
- Security  
    提供声明式的安全访问控制解决方案的安全框架
- OAuth2  
    一种授权框架，提供了一套详细的授权机制。用户或应用可以通过公开的或私有的设置，授权第三方应用访问特定资源。
- JWT
    提供了一种用于发布接入令牌（Access Token),并对发布的签名接入令牌进行验证的方法。 令牌（Token）本身包含了一系列声明，应用程序可以根据这些声明限制用户对资源的访问。
- Config  
    配置文件统一管理

## 开发环境
- node v8.11.4
- redis-5.x
- jdk1.8
- 10.2.15-MariaDB-10.2.15+maria~jessie
- maven3.X
- IntelliJ IDEA 
- vscode


## 开发运行项目
#### 前端开发运行  
安装node-v6.11.0-x64.msi  
```
npm config set registry https://registry.npm.taobao.org
npm install -g @angular/cli
cd PConnect\PConnect-angular
npm install
ng serve
```

#### 后台开发运行 

1. 启动一个redis服务
2. 首次运行，后台启动前先在连接的mysql数据库中建立pconnect_dev、pconnect_auth_dev、ry_dev三个空数据库
3. 在pconnect-user,pconnect-dbcreate、ruoyi的项目中配置好mysql的数据库连接(目前ry_dev首次生成要在ruoyi项目中使用mvn compile flyway:migrate命令，后期追加sql变更则可以直接运行项目自动变更)
4. 然后依次启动：

    - CenterBootstrap  
    - GateBootstrap  
    - UserBootstrap  
    - DBCreateBootstrap  
    - TodoBootstrap  
    - RuoYiApplication

5. 每次开发的时候也不是需要启动所有子项目，只需要启动必须启动的CenterBootstrap、GateBootstrap、UserBootstrap，再加上需要编码调试的对应项目。

#### 访问
```
前端项目： http://localhost:4200 
服务发现： http://127.0.0.1:8961
SwaggerAPI列表聚合： http://localhost:8965/swagger-ui.html
```
需要注意： 每个功能页面要在菜单中出现并正常访问，需要在“菜单管理”功能中进行配置，并且还要给访问的账号角色配置对应的权限，所以有时候新做的页面没来得及将其配置信息做到数据库初始化脚本中，请大家在这时候自行在前端路由代码中找到相应网页链接，然后在“菜单管理”中配置好，然后再给对应角色赋予权限，才能看到新开发的页面。

## 打包部署

### 手动方式

在根目录运行
```
./mvnw install
```

然后依照启动顺序执行
```
java -jar {jar包名称}
```

### docker方式本机部署

运行根目录下面的deploy-to-docker.sh文件
```
./deploy-to-docker.sh
```

### All in One脚本

待续

## 框架整合计划：

| 技术条目 | 待整合 | 已整合 |
| --- | --- | --- |
| angualr |  | * |
| Spring Cloud |  | * |
| OAuth2 |  | * |
| jwt |  | * |
| Spring Cloud Security |  | * |
| Eureka |  | * |
| Zuul |  | * |
| Hystrix |  | * |
| Feign |  | * |
| Ribbon |  | * |
| Redis |  | * |
| Redis Session |  | * |
| Security |  | * |
| Mybatis |  | * |
| Mysql |  | * |
| Swagger |  | * |
| Config |  | * |
| Flyway |  | * |
| Docker部署 |  | * |
| docker-compose |  | * |

## 功能规划      

| 功能 | 计划 | 已完成 |
| --- | --- | --- |
| 用户管理 |  | * |
| 菜单管理 Cloud |  | * |
| 组织类型管理 |  | * |
| 组织架构管理————组织管理、关联用户、组织授权 |  | * |
| 数据字典 |  | * |
| 日志管理 |  | * |
| todo管理 |  | * |
| 词汇表管理 |  | * |
| 知识库管理 | * |  |
| 选择题维护 | * |  |
| 盘点管理 | * |  |
| 插件管理 | * |  |
  

### 非功能任务列表：

* Mysql配置成SSL连接


## 效果展示

