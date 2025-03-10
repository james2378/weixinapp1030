### 介绍
java毕业设计，微信小程序健身房私教预约系统
### 3000多套系统，需要联系
抠：3565014707 微：a13424421017

#### 软件架构
##### 整体架构模式
这是一个 多端协同的健身/课程管理系统，采用 前后端分离架构，包含以下模块：

微信小程序端（mp-weixin）：面向用户，提供课程预约、订单管理等功能。

管理后台（ssm45k9p/src/main/webapp/admin）：基于 Vue.js + ElementUI 的后台管理系统。

后端服务（ssm45k9p）：基于 Spring Boot + MyBatis 的 Java 服务，提供统一 API。

H5用户端（ssm45k9p/src/main/webapp/front）：基于 uni-app 的跨端应用（支持 H5 和小程序）。
##### 分层架构设计
后端分层（ssm45k9p）：

Controller层：controller 包（如 CommonController）处理 HTTP 请求，接口统一返回 JSON 数据。

Service层：service 包（CommonService）封装核心业务逻辑，如订单结算、课程预约。

DAO层：dao 包（CommonDao）通过 MyBatis XML 映射文件（CommonDao.xml）操作数据库。

实体与数据模型：

entity 包定义数据库实体（如 DingdanxinxiModel 订单信息）；

vo（值对象）和 view（视图模型）用于接口数据传输。

前端分层（以微信小程序为例）：

视图层：pages 目录定义页面（如 kechengyuyue 课程预约页），通过 .wxml + .wxss 实现界面。

组件层：components 封装可复用组件（如 mescroll-uni 滚动加载组件）。

状态管理：通过全局变量或轻量级状态库（如 store.js）管理用户登录状态。
##### 关键技术特性
多端适配：

微信小程序端使用原生组件（如 w-picker 时间选择器）；H5 端复用 uni-app 跨端组件（如 uni-calendar）。

权限控制：

后端通过 AuthorizationInterceptor 拦截器校验用户权限；

前端管理后台通过路由（router-static.js）控制页面访问。

第三方服务集成：
BaiduUtil 可能用于地图定位或 AI 能力（如人脸识别签到）。
#### 核心功能模块解析
##### 用户端功能（微信小程序 + H5）
课程预约与订单管理：

kechengyuyue（课程预约）：用户选择健身课程并提交预约。

dingdanxinxi（订单信息）：查看订单详情及支付状态。

tuikuanxinxi（退款信息）：处理订单退款申请。

会员服务：
huiyuan（会员管理）：用户注册、会员卡绑定与权益查询。

user-info（用户信息）：修改个人信息、查看健身记录。

数据统计：
yuejiesuantongji（月结算统计）：教练或管理员查看月度收益。

zongjiesuantongji（总结算统计）：全局销售数据分析。
##### 管理后台功能（Vue.js）
课程管理：
jianshenkecheng（健身课程）：管理课程名称、教练、时间安排。
kechengfenlei（课程分类）：定义课程类型（如瑜伽、搏击）。

教练与会员管理：
jiaolian（教练管理）：维护教练信息及排班计划。
users（用户管理）：审核会员注册、禁用违规账户。

系统配置：
config（参数配置）：设置支付方式、课程预约规则等。
##### 后端核心服务
通用业务逻辑：

CommonController 提供通用 CRUD 接口，支持动态 SQL（CommonDao.xml）。

MyMetaObjectHandler 实现 MyBatis-Plus 自动填充（如创建时间、更新时间）。

支付与结算：

集成支付宝/微信支付（config.properties 存储支付密钥）；

定时任务生成月结报表（yuejiesuantongji）。
