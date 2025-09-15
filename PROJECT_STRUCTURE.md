# Spring AI Alibaba A2A Server - 项目结构

## 📁 目录结构

```
src/main/java/runtime/
├── A2aServerApplication.java          # Spring Boot 启动入口
├── engine/                           # 引擎层：对外接口、配置装配、记忆与通用服务
│   ├── controller/                      # REST/JSON-RPC 控制器
│   │   ├── A2aController.java           # A2A 协议处理入口
│   │   ├── AgentCardController.java     # Agent 卡片管理接口
│   │   ├── AgentController.java         # Agent 基础接口
│   │   └── MemoryController.java        # 记忆/会话接口
│   ├── infrastructure/                  # 基础设施与外部系统集成
│   │   ├── config/                      # 配置装配（属性、YAML、Bean）
│   │   │   ├── agent/                   # Agent 相关配置
│   │   │   ├── core/                    # 运行时核心配置
│   │   │   ├── memory/                  # 内存服务配置
│   │   │   └── nacos/                   # Nacos 配置
│   │   └── external/                    # 外部系统适配
│   │       ├── nacos/                   # Nacos 注册/发现集成
│   │       └── registry/                # Agent 注册抽象与实现
│   ├── memory/                           # 记忆与会话领域
│   │   ├── context/                     # 上下文编排与管理
│   │   ├── dto/                         # 记忆与会话 DTO
│   │   ├── model/                       # 领域模型（消息、会话、类型）
│   │   ├── persistence/                 # 存储实体、仓储与实现
│   │   └── service/                     # 记忆/嵌入/会话服务
│   ├── service/                          # 引擎通用服务
│   │   ├── GraphAgentExecutor.java      # 基于图的 Agent 执行器
│   │   ├── JSONRPCHandler.java          # JSON-RPC 消息处理
│   │   └── MemoryServiceStartupListener.java # 启动期初始化
│   └── shared/                           # 共享服务抽象与生命周期管理
│       ├── Service.java
│       ├── ServiceManager.java
│       └── ServiceWithLifecycleManager.java
└── sandbox/                            # 受控执行沙箱与工具
    ├── manager/                          # 沙箱/容器管理与资源清理
    │   ├── DockerManager.java
    │   ├── SandboxCleanupService.java
    │   ├── SandboxManager.java
    │   ├── model/                       # 容器/类型/卷等模型
    │   └── util/                        # HTTP 客户端、随机串等
    └── tools/                            # 面向 Agent 的工具集合
        ├── base/                        # 工具基类/契约
        ├── browser/                     # 浏览器与页面操作工具
        ├── fs/                          # 文件系统读写工具
        ├── model/                       # 工具请求/响应模型
        ├── SandboxTools.java            # 工具集合装配
        └── ToolsInit.java               # 工具初始化入口
```