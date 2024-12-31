> #### 作者主页：[舒克日记](https://blog.csdn.net/cativen)
>
>  简介：Java领域优质创作者、Java项目、学习资料、技术互助
>
> <b><font color=red>文中获取源码</font></b>

# 项目介绍

本系统分为管理员、会员、商家三个角色

管理员登录使用本系统涉到的功能主要有个人中心、会员管理、商家管理、商品分类管理、商品信息管理、农产品监督管理、助农信息管理、留言板、系统管理、订单管理等功能。

会员登录使用本系统涉到的功能主要有首页、商品信息、农产品监督、公告信息、留言板、购物车、个人中心等功能。

商家登录使用本系统涉到的功能主要有个人中心、商品信息管理、农产品监督管理、助农信息管理、订单管理等功能。

# 环境要求

1.运行环境：最好是java jdk1.8,我们在这个平台上运行的。其他版本理论上也可以。

2.IDE环境：IDEA,Eclipse,Myeclipse都可以。推荐IDEA;

3.tomcat环境：Tomcat7.x,8.X,9.x版本均可

4.硬件环境：windows7/8/10 4G内存以上；或者Mac OS;

5.是否Maven项目：是；查看源码目录中是否包含pom.xml;若包含，则为maven项目，否则为非maven.项目

6.数据库：MySql5.7/8.0等版本均可；

# 技术栈

运行环境：jdk8 + tomcat9 + mysql5.7 + windows10

服务端技术：Java、Spring、SpringMVC、Mybatis，SSM

前端：jsp

# 使用说明

1.使用Navicati或者其它工具，在mysql中创建对应sq文件名称的数据库，并导入项目的sql文件；

2.使用IDEA/Eclipse/MyEclipse导入项目，修改配置，运行项目；

3.将项目中config-propertiesi配置文件中的数据库配置改为自己的配置，然后运行；

# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq

源码看好后直接在网站付款下单即可，付款成功会自动弹出百度网盘链接，网站地址：[http://www.codegym.top](http://www.codegym.top/)

其它问题请关注公众号：**IT小舟**,关注后发送消息即可，都会给您回复的。若没有及时回复请耐心等待，通常当天会有回复

# 运行截图

## 功能模块截图

![img](https://i-blog.csdnimg.cn/img_convert/6b02d423fe7ec9f17195a69f9daa5b55.png)

![img](https://i-blog.csdnimg.cn/img_convert/1543c4a7052600ba039597931041d58b.png)

![img](https://i-blog.csdnimg.cn/img_convert/5cfcc0861d121e5bdfe3348b343dcdab.png)

### 项目截图

前台

![jspm农业电商服务系统302496](https://i-blog.csdnimg.cn/img_convert/20d63ba32112831ac7e271b2d2aa2e92.png)

![jspm农业电商服务系统302499](https://i-blog.csdnimg.cn/img_convert/7b956bd7f07eb29b4adaa8b2c1690957.png)

![jspm农业电商服务系统302495](https://i-blog.csdnimg.cn/img_convert/ca27f2c50c3efa4005ad44be9068210a.png)

后台

![jspm农业电商服务系统302498](https://i-blog.csdnimg.cn/img_convert/adf24218eb226054a75e628aa4a91b29.png)

![jspm农业电商服务系统3024910](https://i-blog.csdnimg.cn/img_convert/b91c45d0a47c539992a13b3ea4a83d49.png)

![jspm农业电商服务系统302493](https://i-blog.csdnimg.cn/img_convert/15e7092565813891b3c5d7e82d556529.png)

![jspm农业电商服务系统302494](https://i-blog.csdnimg.cn/img_convert/8cbe9d4e44118c0945d455c053e67ea6.png)

### 代码

```
  UserTenancyDO userTenancyDO = new UserTenancyDO();
        userTenancyDO.setUserId(customerId);
        userTenancyDO.setTenantId(tenantId);
        userTenancyDO.setStatus(CommonStatusEnum.ENABLE.status());
        userTenancyDO.setCreatorId(BUSINESS_TYPE_CLIFE);
        userTenancyDO.setCreateTime(System.currentTimeMillis());
        userTenancyDO.setStatus(1);

        //查询sort排序最后一个
        LambdaQueryWrapper<UserTenancyDO> userTenancyDOLambdaQueryWrapper = new LambdaQueryWrapper<>();
        userTenancyDOLambdaQueryWrapper.eq(UserTenancyDO::getUserId, customerId);
        userTenancyDOLambdaQueryWrapper.orderByDesc(UserTenancyDO::getSort);
        userTenancyDOLambdaQueryWrapper.last("limit 1");
        UserTenancyDO one = userTenancyMapper.selectOne(userTenancyDOLambdaQueryWrapper);
        Integer sort = one == null ? 0 : one.getSort() + 1;
        userTenancyDO.setSort(sort);
        userTenancyDO.setEmail(email);
        userTenancyDO.setTbUserId(tbUserId);
        String tenantNameById = tenantServiceGateway.getTenantNameById(tenantId);
        userTenancyDO.setTenantName(tenantNameById);
        userTenancyDO.setIsAdmin(0);
        userTenancyMapper.insert(userTenancyDO);
```
