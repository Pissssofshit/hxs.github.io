## 是什么？
mPaaS的设想是作为支撑应用开发、测试、错误修复全生命周期的统一平台
整合现有系统，打通应用数据；

系统整合:
    对外的接口: 网关
    系统间的通信: grpc?
打通应用数据:
    统一数据定义
 
## 用到了什么微服务技术？
网关 get
配置中心: apollo
服务发现: k8s自带
通讯方式: 系统间grpc,前端http
监控预警: 计划promethus
熔断、隔离、限流、降级: 内部服务，没有到这一步
容器与服务编排引擎: 啥玩意?

