## :closed_lock_with_key::busts_in_silhouette: 一个简洁优美的权限管理系统

### 项目简介
*:sparkles: 如你所见 : 这或许是流程最清晰、代码最干净、注释最详细、配置最简单的 Shiro 项目啦 ! 非常适合进阶学习 SpringBoot 与 Shiro 的同学，是一个非常具有参考与学习价值的权限管理项目啦~*


### 开发环境

| 工具    | 版本或描述                      |    
| ------- | ----------------------------- |    
| `OS`    | Windows 7 / 10                | 
| `JDK`   | 1.7+ / 11+                    |    
| `IDE`   | IntelliJ IDEA 2017.3 / 2019.1 |    
| `Maven` | 3.3.1 / 3.6.0                 |    
| `MySQL` | 5.6.4 / 8.0.0+                |



### 项目模块划分

| 模块          | 释义                                       |    
| ------------- | ------------------------------------------ |    
| `shiro-core`  | 核心业务类模块，提供基本的数据操作、工具处理等 |    
| `shiro-admin` | 后台管理模块                                |    



### 数据库模型
![sql model](https://raw.githubusercontent.com/YUbuntu0109/springboot-shiro/master/docs/img/sql-model.png)



### 使用说明
1. 使用`IDE`导入本项目
2. 新建数据库`CREATE DATABASE shiro;`
3. 导入数据库`docs/db/shiro.sql`
4. 修改(`resources/application.yml`)配置文件
   1. 数据库链接属性(可搜索`datasource`或定位到L.19) 
   2. redis配置(可搜索`redis`或定位到L.69)
5. 运行项目(三种方式)
   1. 项目根目录下执行`mvn -X clean package -Dmaven.test.skip=true`编译打包，然后执行`java -jar shiro-admin/target/shiro-admin.jar`
   2. 项目根目录下执行`mvn springboot:run`
   3. 直接运行`ShiroAdminApplication.java`
6. 浏览器访问`http://127.0.0.1:8080`

#### 用户密码
> 超级管理员 : 账号：`root` , 密码 : `123456`

> 普通管理员 : 账号：`admin` , 密码 : `123456`

#### Druid监控
> 链接 : `http://127.0.0.1:8080/druid/index.html`

> 用户名 : `zyd-druid` , 密码 : `zyd-druid`



### 项目结构
```
│  .gitignore
│  LICENSE
│  pom.xml
│  README.md
│
├─docs
│  ├─db
│  │      shiro.sql
│  │
│  └─img
│          admin-resource.PNG
│          admin-role.PNG
│          admin-user.PNG
│          db-datasource.PNG
│          db-login.PNG
│          index.PNG
│          login.PNG
│          role-role[admin].PNG
│          root-resource.PNG
│          root-role-[root].PNG
│          root-role.PNG
│          root-user.PNG
│          sql-model.png
│
├─shiro-admin
│  │  .gitignore
│  │  pom.xml
│  │
│  └─src
│      ├─main
│      │  ├─java
│      │  │  └─com
│      │  │      └─zyd
│      │  │          └─shiro
│      │  │              │  ShiroAdminApplication.java
│      │  │              │
│      │  │              └─controller
│      │  │                      ErrorPagesController.java
│      │  │                      ExceptionHandleController.java
│      │  │                      PassportController.java
│      │  │                      RenderController.java
│      │  │                      RestResourcesController.java
│      │  │                      RestRoleController.java
│      │  │                      RestUserController.java
│      │  │
│      │  └─resources
│      │      │  application.yml
│      │      │  logback.xml
│      │      │
│      │      ├─static
│      │      │  └─assets
│      │      │      ├─css
│      │      │      │      zhyd.core.css
│      │      │      │
│      │      │      ├─images
│      │      │      │      default-portrait.png
│      │      │      │      favicon.ico
│      │      │      │      loading.gif
│      │      │      │
│      │      │      └─js
│      │      │              jquery-form.js
│      │      │              validator.js
│      │      │              zhyd.core.js
│      │      │              zyd.table.js
│      │      │              zyd.tool.js
│      │      │
│      │      └─templates
│      │          │  index.ftl
│      │          │  login.ftl
│      │          │
│      │          ├─error
│      │          │      401.ftl
│      │          │      403.ftl
│      │          │      404.ftl
│      │          │      500.ftl
│      │          │
│      │          ├─layout
│      │          │      footer.ftl
│      │          │      header.ftl
│      │          │      setting.ftl
│      │          │      sidebar.ftl
│      │          │
│      │          ├─resources
│      │          │      list.ftl
│      │          │
│      │          ├─role
│      │          │      list.ftl
│      │          │
│      │          └─user
│      │                  list.ftl
│      │
│      └─test
│          └─java
│              └─com
│                  └─zyd
│                      └─shiro
│                              ShiroAdminApplicationTests.java
│
└─shiro-core
    │  .gitignore
    │  pom.xml
    │
    └─src
        ├─main
        │  ├─java
        │  │  └─com
        │  │      └─zyd
        │  │          └─shiro
        │  │              ├─business
        │  │              │  ├─consts
        │  │              │  │      CommonConst.java
        │  │              │  │      SessionConst.java
        │  │              │  │
        │  │              │  ├─entity
        │  │              │  │      Resources.java
        │  │              │  │      Role.java
        │  │              │  │      RoleResources.java
        │  │              │  │      User.java
        │  │              │  │      UserRole.java
        │  │              │  │
        │  │              │  ├─enums
        │  │              │  │      ResourceTypeEnum.java
        │  │              │  │      ResponseStatus.java
        │  │              │  │      UserGenderEnum.java
        │  │              │  │      UserStatusEnum.java
        │  │              │  │      UserTypeEnum.java
        │  │              │  │
        │  │              │  ├─service
        │  │              │  │  │  ShiroService.java
        │  │              │  │  │  SysResourcesService.java
        │  │              │  │  │  SysRoleResourcesService.java
        │  │              │  │  │  SysRoleService.java
        │  │              │  │  │  SysUserRoleService.java
        │  │              │  │  │  SysUserService.java
        │  │              │  │  │
        │  │              │  │  └─impl
        │  │              │  │          ShiroServiceImpl.java
        │  │              │  │          SysResourcesServiceImpl.java
        │  │              │  │          SysRoleResourcesServiceImpl.java
        │  │              │  │          SysRoleServiceImpl.java
        │  │              │  │          SysUserRoleServiceImpl.java
        │  │              │  │          SysUserServiceImpl.java
        │  │              │  │
        │  │              │  ├─shiro
        │  │              │  │  ├─credentials
        │  │              │  │  │      CredentialsMatcher.java
        │  │              │  │  │      RetryLimitCredentialsMatcher.java
        │  │              │  │  │
        │  │              │  │  └─realm
        │  │              │  │          ShiroRealm.java
        │  │              │  │
        │  │              │  └─vo
        │  │              │          ResourceConditionVO.java
        │  │              │          RoleConditionVO.java
        │  │              │          UserConditionVO.java
        │  │              │
        │  │              ├─framework
        │  │              │  ├─config
        │  │              │  │      DruidConfig.java
        │  │              │  │      ErrorPagesConfig.java
        │  │              │  │      FreeMarkerConfig.java
        │  │              │  │      MybatisConfig.java
        │  │              │  │      RedisConfig.java
        │  │              │  │      ShiroConfig.java
        │  │              │  │      WebMvcConfig.java
        │  │              │  │
        │  │              │  ├─exception
        │  │              │  │      ZhydException.java
        │  │              │  │
        │  │              │  ├─holder
        │  │              │  │      RequestHolder.java
        │  │              │  │      SpringContextHolder.java
        │  │              │  │
        │  │              │  ├─interceptor
        │  │              │  │      RememberAuthenticationInterceptor.java
        │  │              │  │
        │  │              │  ├─object
        │  │              │  │      AbstractBO.java
        │  │              │  │      AbstractDO.java
        │  │              │  │      AbstractService.java
        │  │              │  │      BaseConditionVO.java
        │  │              │  │      PageResult.java
        │  │              │  │      ResponseVO.java
        │  │              │  │
        │  │              │  ├─property
        │  │              │  │      DruidProperties.java
        │  │              │  │      RedisProperties.java
        │  │              │  │
        │  │              │  ├─redis
        │  │              │  │      CustomRedisManager.java
        │  │              │  │
        │  │              │  ├─runner
        │  │              │  │      BlogApplicationRunner.java
        │  │              │  │
        │  │              │  └─tag
        │  │              │          CustomTagDirective.java
        │  │              │
        │  │              ├─persistence
        │  │              │  ├─beans
        │  │              │  │      SysResources.java
        │  │              │  │      SysRole.java
        │  │              │  │      SysRoleResources.java
        │  │              │  │      SysUser.java
        │  │              │  │      SysUserRole.java
        │  │              │  │
        │  │              │  └─mapper
        │  │              │          SysResourceMapper.java
        │  │              │          SysRoleMapper.java
        │  │              │          SysRoleResourcesMapper.java
        │  │              │          SysUserMapper.java
        │  │              │          SysUserRoleMapper.java
        │  │              │
        │  │              ├─plugin
        │  │              │      BaseMapper.java
        │  │              │
        │  │              └─util
        │  │                      AesUtil.java
        │  │                      IpUtil.java
        │  │                      Md5Util.java
        │  │                      PasswordUtil.java
        │  │                      ResultUtil.java
        │  │                      SessionUtil.java
        │  │
        │  └─resources
        │      └─mybatis
        │              SysResourceMapper.xml
        │              SysRoleMapper.xml
        │              SysUserMapper.xml
        │              SysUserRoleMapper.xml
        │
        └─test
            └─java
                └─com
                    └─zyd
                        └─shiro
                                ListUtilTest.java
                                ShiroCoreApplicationTests.java
```



### 图片预览
*:camera_flash: 用户登录页*

![用户登录](https://raw.githubusercontent.com/YUbuntu0109/springboot-shiro/master/docs/img/login.PNG)

*:camera_flash: 系统首页*

![首页](https://raw.githubusercontent.com/YUbuntu0109/springboot-shiro/master/docs/img/index.PNG)

*:camera_flash: 资源管理页*

![资源管理](https://raw.githubusercontent.com/YUbuntu0109/springboot-shiro/master/docs/img/root-resource.PNG)

*:camera_flash: 角色管理页*

![角色管理](https://raw.githubusercontent.com/YUbuntu0109/springboot-shiro/master/docs/img/root-role.PNG)

*:camera_flash: 为角色分配资源*

![角色分配资源](https://raw.githubusercontent.com/YUbuntu0109/springboot-shiro/master/docs/img/root-role-%5Broot%5D.PNG)

*:camera_flash: 用户管理页*

![用户管理](https://raw.githubusercontent.com/YUbuntu0109/springboot-shiro/master/docs/img/root-user.PNG)

*:camera_flash: 为用户分配角色*

![用户分配角色](https://raw.githubusercontent.com/YUbuntu0109/springboot-shiro/master/docs/img/root-user%5Brole%5D.PNG)

> 注 : 以上图片为`root`用户登录后的部分截屏，`admin`用户的界面请参考`docs/img`下的图片哟~



### 参考资料
1. *本项目部分代码参考自网络文章 : [查看原文链接](http://blog.csdn.net/poorcoder_/article/details/71374002)*    
2. *前端模板来源自开源模板 : [查看模板链接](https://colorlib.com/polygon/gentelella/index.html)，[查看开源项目](https://github.com/puikinsh/gentelella)*
3. 部分js实现参考开源项目 : [查看开源项目](https://gitee.com/yadong.zhang/DBlog)
