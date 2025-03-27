# Multilogin 插件安装与配置完全指南

## 1. 项目目录结构解析

Multilogin 采用标准化的Gradle项目结构，以下是核心目录和文件说明：

Multilogin/
├── api/          # API接口模块
├── bukkit/       # Bukkit服务端适配
├── bungee/       # BungeeCord代理适配
├── core/         # 核心功能实现
├── flows/        # 业务流程控制
├── velocity/     # Velocity代理适配
└── 其他配置文件...

### 关键目录功能
- **核心模块**：
  - `core/`：包含账户验证、会话管理等核心逻辑
  - `api/`：提供开发者扩展接口
- **服务端适配**：
  - `bukkit/`：支持Spigot/Paper等衍生服务端
  - `bungee/` & `velocity/`：代理服务器专用模块
- **构建配置**：
  - `build.gradle`：定义项目依赖和构建流程
  - `settings.gradle`：多模块项目管理

👉 [【点击查看】2025年最新 Multilogin 优惠码及特价套餐活动方案汇总](https://bit.ly/multIlogin)

## 2. 插件安装流程详解

### 三步快速安装
1. **获取插件包**  
   从官方渠道获取最新版`.jar`文件（推荐版本≥2.3.1）

2. **部署到服务器**  
   bash
   # Bukkit系服务端
   cp MultiLogin.jar /path/to/plugins/
   
   # BungeeCord代理端
   cp MultiLogin.jar /path/to/plugins/
   

3. **启动验证**  
   观察启动日志确认加载成功：
   
   [Multilogin] Successfully enabled v2.3.1
   

## 3. 核心配置优化指南

`config.yml`示例配置（带注释说明）：

yaml
# 基础设置
serverName: "MyAwesomeServer"  # 显示在登录界面

# 认证系统配置
authSystem:
  type: "mixed"  # [local|external|mixed]
  timeout: 30    # 认证超时(秒)

# 外置认证服务器
externalAuth:
  - name: "主认证节点"
    url: "https://auth.example.com/api"
    retry: 3      # 失败重试次数

### 配置技巧
- 启用`connection-pooling`可提升高并发性能
- 建议设置`session-timeout: 3600`保持长效会话
- 生产环境务必配置`backup-servers`实现故障转移

## 4. 高级功能配置

通过`advanced.yml`可启用：
- IP地理围栏限制
- 自定义登录流程
- 实时监控集成
- 多语言支持

> 提示：完整配置文档可通过`/ml docs`命令在游戏内查看