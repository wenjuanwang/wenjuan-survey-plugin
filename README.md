# wenjuan-survey

wenjuan-survey 是一个面向 Claude Code 的问卷网插件，用于通过问卷网 MCP 服务完成问卷调查、考试测评、收集表单、投票评选、满意度调查、在线收款、360 评估等场景下的项目创建、题目修改、数据查看与导出。

`wenjuan-survey` is a Claude Code plugin for Wenjuan workflows through the Wenjuan MCP service, including surveys, exams and assessments, collection forms, voting campaigns, satisfaction studies, online payment forms, and 360 reviews.

## 插件能力

该插件可通过问卷网 MCP 服务支持以下典型场景：

- 问卷调查
- 考试测评
- 收集表单
- 投票评选
- 满意度调查
- 在线收款
- 360 评估

在这些场景下，插件主要提供三类高频能力：

- 创建项目：创建上述场景对应的项目
- 修改题目：增删改已有项目中的题目结构
- 查看数据：查看报告、概览指标，并导出原始数据

内置 skills：

- `/wenjuan-survey:setup`：查看插件配置与使用指引
- `/wenjuan-survey:create-survey`：创建问卷调查、考试测评、收集表单、投票评选、满意度调查、在线收款、360 评估等项目
- `/wenjuan-survey:update-question`：更新题目结构
- `/wenjuan-survey:view-data`：查看项目数据、报告与导出能力

通过该插件可直接调用问卷网的以下能力：

- 创建、查询、更新项目，以及查看项目结构
- 创建、更新、删除题目
- 发布问卷与停止收集
- 获取报告页面
- 查看概览指标
- 导出原始数据

## 使用前提

在开始前，请确认你具备以下条件：

- 已安装并可正常使用 Claude Code
- 可以访问远程 MCP 服务 `https://mcp.wenjuan.com`
- 已拥有问卷网账号，并可获取 `WJ-API-Key`

## 安装方式

### 方式一：通过自有 Marketplace 安装

如果你们已经搭建了自己的 Claude Code plugin marketplace，可直接从 marketplace 安装 `wenjuan-survey`，然后在插件设置中填写 `WJ-API-Key`。

安装后如当前会话未自动生效，可运行：

```bash
/reload-plugins
```

### 方式二：本地目录加载

如果你是在本地开发、测试，或临时分发插件，可直接通过插件目录加载：

```bash
claude --plugin-dir /path/to/wenjuan-survey-plugin
```

## 配置方式

用户不需要手动编辑任何 JSON 或配置文件。

首次使用时，只需要在 Claude Code 中配置一次 `WJ-API-Key`。Claude 会保存该插件设置，后续会话通常无需重复配置，除非密钥被修改或清除。

获取密钥方式：

1. 登录 `www.wenjuan.com`
2. 进入 `个人中心 => API 对接 => MCP 对接`
3. 复制 `WJ-API-Key`

在 Claude Code 中完成配置：

1. 运行 `/plugins`
2. 找到 `wenjuan-survey` 插件
3. 打开插件设置（Configure options）
4. 在 `WJ-API-Key` 输入框中仅粘贴密钥值本身
5. 保存设置
6. 如当前会话未自动生效，运行 `/reload-plugins`

## 推荐使用方式

推荐先运行：

```text
/wenjuan-survey:setup
```

然后根据你的目标继续使用：

- 创建项目：`/wenjuan-survey:create-survey`
- 修改题目：`/wenjuan-survey:update-question`
- 查看数据：`/wenjuan-survey:view-data`

## 插件目录结构

```text
.
├── .claude-plugin/
│   └── plugin.json
├── .mcp.json
├── skills/
│   ├── create-survey/
│   │   └── SKILL.md
│   ├── setup/
│   │   └── SKILL.md
│   ├── update-question/
│   │   └── SKILL.md
│   └── view-data/
│       └── SKILL.md
└── README.md
```

## 建议的冒烟测试

建议优先验证只读链路：

- 对一个已知项目运行 `/wenjuan-survey:view-data`
- 确认插件可以成功访问项目列表、项目结构、报告或概览数据

如需进一步验证写入链路，建议仅在测试项目中执行：

- 使用 `/wenjuan-survey:create-survey` 创建测试项目
- 使用 `/wenjuan-survey:update-question` 修改测试题目

## 排查建议

如果插件安装后无法正常工作，可按以下方向排查：

- 检查是否已正确配置 `WJ-API-Key`
- 检查当前网络是否可以访问 `https://mcp.wenjuan.com`
- 运行 `/reload-plugins` 重新加载插件
- 重新打开 `/plugins` 确认配置已保存

## 说明

- `.claude-plugin/plugin.json` 存放插件元数据和用户配置 schema
- `.mcp.json` 位于插件根目录，用于声明问卷网 MCP 服务连接方式
- 该插件仅引用插件目录内部文件，以兼容 Claude 的插件缓存行为
- 该仓库既可用于本地开发测试，也可作为自有 marketplace 分发的插件包来源
