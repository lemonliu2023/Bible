# Cursor 代码补全模型配置指南

## 概述

Cursor 是一款基于 AI 的代码编辑器，支持多种 AI 模型进行代码补全和智能编程辅助。本指南将详细介绍如何更改和配置 Cursor 的代码补全模型。

## 1. 模型选择与切换

### 1.1 内置模型选择

Cursor 默认提供以下模型：

1. **GPT-4o** - OpenAI 最新模型，智能程度高
2. **GPT-4** - OpenAI 经典模型，平衡性能与质量
3. **Claude 3.5 Sonnet** - Anthropic 的高性能模型
4. **cursor-small** - Cursor 自定义模型，速度快，无限制使用

### 1.2 切换模型方法

**方法一：通过下拉菜单**
1. 在 AI 输入框下方，您会看到模型选择下拉菜单
2. 点击下拉菜单选择想要使用的模型
3. 选择后即时生效

**方法二：通过设置界面**
1. 使用快捷键 `Ctrl+Shift+P` (Windows/Linux) 或 `⌘+Shift+P` (Mac) 打开命令面板
2. 搜索 "Models" 或 "模型"
3. 在设置中选择默认模型

## 2. 自定义 API 密钥配置

### 2.1 支持的 API 提供商

Cursor 支持以下 API 提供商的自定义密钥：

- **OpenAI** - GPT 系列模型
- **Anthropic** - Claude 系列模型  
- **Google** - Gemini 系列模型
- **Azure** - Azure OpenAI 服务
- **OpenRouter** - 多模型聚合平台

### 2.2 配置步骤

**步骤1：打开设置**
```
Ctrl/⌘ + Shift + J → Models → API Keys
```

**步骤2：添加 API 密钥**

**OpenAI API 密钥：**
1. 访问 [OpenAI Platform](https://platform.openai.com/api-keys)
2. 创建新的 API 密钥
3. 在 Cursor 设置中粘贴密钥
4. 点击 "Verify" 验证

**Anthropic API 密钥：**
1. 访问 [Anthropic Console](https://console.anthropic.com/)
2. 获取 API 密钥
3. 在 Cursor 中配置 Anthropic API Key

**OpenRouter 配置：**
1. 注册 [OpenRouter 账户](https://openrouter.ai/keys)
2. 获取 API 密钥
3. 在 OpenAI API 密钥字段中使用 OpenRouter 密钥
4. 可访问多种模型如 DeepSeek、Llama 等

### 2.3 模型定价参考

| 模型 | 输入价格 | 输出价格 | 特点 |
|------|----------|----------|------|
| GPT-4o | $2.50/1M tokens | $10.00/1M tokens | 最新最强 |
| Claude 3.5 Sonnet | $3.00/1M tokens | $15.00/1M tokens | 代码理解强 |
| DeepSeek Coder | $0.14/1M tokens | $0.28/1M tokens | 性价比高 |
| cursor-small | 免费 | 免费 | 速度快，无限制 |

## 3. 中文界面与回复设置

### 3.1 界面中文化

**方法一：安装中文语言包**
1. 按 `Ctrl/⌘ + Shift + X` 打开扩展商店
2. 搜索 "Chinese" 或 "中文"
3. 安装 "Chinese (Simplified) Language Pack for Visual Studio Code"
4. 重启 Cursor

**方法二：手动切换语言**
1. 按 `Ctrl/⌘ + Shift + P` 打开命令面板
2. 输入 "Configure Display Language"
3. 选择 "zh-cn"
4. 重启应用

### 3.2 设置 AI 中文回复

**全局中文回复设置：**
1. 打开设置：`Ctrl/⌘ + Shift + J`
2. 找到 "Features > Chat" 部分
3. 在 "默认提示词" (Default prompt) 中添加：
```
请用中文回复所有问题
```

**临时中文回复：**
在聊天时输入以下任一指令：
- `ZH-CN ONLY`
- `始终用中文回答`
- `请用中文回复`

### 3.3 项目级中文配置

创建 `.cursorrules` 文件：
```
你是一个中文编程助手。请遵循以下规则：

1. 始终使用中文回复
2. 代码注释使用中文
3. 错误解释用中文描述
4. 提供中英文术语对照

代码风格：
- 函数名和变量名使用英文
- 注释和文档使用中文
- 保持代码简洁易读
```

## 4. 高级配置

### 4.1 Tab 代码补全设置

在设置中可以配置：
- **Cursor Tab**: 启用/禁用智能补全
- **Partial Accepts**: 部分接受建议的快捷键
- **Auto Import**: 自动导入设置
- **Context Length**: 上下文长度限制

### 4.2 隐私与安全设置

**重要安全配置：**
```json
{
  "allowAiService": false,        // 禁止代码上传到AI服务
  "telemetry.enableTelemetry": false  // 关闭遥测数据收集
}
```

### 4.3 性能优化

**排除文件监控：**
```json
{
  "search.exclude": {
    "**/target": true,
    "**/*.jar": true,
    "**/*.class": true
  },
  "files.watcherExclude": {
    "**/target/**": true,
    "**/node_modules/**": true
  }
}
```

## 5. 常见问题解决

### Q1: API 密钥无法验证？
**解决方案：**
- 确认密钥格式正确
- 检查网络连接
- 验证 API 配额是否充足

### Q2: 模型响应速度慢？
**解决方案：**
- 切换到 cursor-small 模型
- 检查网络连接
- 减少上下文长度

### Q3: 中文回复不稳定？
**解决方案：**
- 在每次对话开始时重新声明语言要求
- 使用 `.cursorrules` 文件设置项目级规则
- 更新到最新版本 Cursor

### Q4: 代码补全不准确？
**解决方案：**
- 等待代码库索引完成
- 增加项目上下文信息
- 尝试不同的模型

## 6. 最佳实践建议

1. **模型选择策略：**
   - 复杂逻辑：使用 GPT-4o 或 Claude 3.5 Sonnet
   - 日常编程：使用 cursor-small
   - 成本敏感：考虑 DeepSeek 等经济型模型

2. **中文使用技巧：**
   - 混合使用中英文提示词
   - 重要术语提供中英对照
   - 保持提示词简洁明确

3. **性能优化：**
   - 定期清理聊天历史
   - 合理设置上下文长度
   - 排除不必要的文件监控

4. **团队协作：**
   - 统一 `.cursorrules` 配置
   - 共享 API 密钥管理策略
   - 建立代码风格规范

## 结语

通过合理配置 Cursor 的模型和相关设置，您可以获得最佳的 AI 编程体验。记住根据具体需求选择合适的模型，并保持配置的及时更新。

如有更多问题，请参考 [Cursor 官方文档](https://docs.cursor.com/) 或访问 [Cursor 官网](https://www.cursor.com/cn)。