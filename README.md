# wenjuan-survey

这是一个用于对接问卷网的 Claude Code 插件，主要提供三类能力：创建问卷项目、修改题目结构、查看项目数据。通过这个插件，你可以直接在 Claude Code 中完成问卷创建、题目增删改、项目发布、数据查看与导出等操作，无需手动调用底层接口。

它适用于多种常见业务场景，包括问卷调查、考试测评、收集表单、投票评选、满意度调查、在线收款、 360 评估等。

插件通过 HTTP 连接远程问卷网 MCP 服务，并按 Claude 插件与 Marketplace 分发要求组织目录结构。

## 这个插件提供什么

- 连接远程 MCP 服务 `https://mcp.wenjuan.com`
- 通过 `WJ-API-Key` 提供更易用的身份认证体验
- 可通过 `/wenjuan-survey:setup` 获取配置指引
- 提供 3 个覆盖常见场景的技能：
  - `/wenjuan-survey:create-survey`：用于创建问卷调查、考试测评、收集表单、投票评选、满意度调查、在线收款、 360 评估等项目
  - `/wenjuan-survey:update-question`：用于修改和优化已有问卷项目中的题目结构
  - `/wenjuan-survey:view-data`：用于查看报告与数据、导出数据
- 可调用问卷网的以下能力：
  - 创建、查询、更新项目，以及查看项目结构
  - 创建、更新、删除题目
  - 发布问卷与停止收集
  - 获取报告页面
  - 查看概览指标
  - 导出原始数据

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

## 身份认证说明

用户不需要手动编辑任何配置文件。

首次使用时，只需要在 Claude Code 里配置一次 `WJ-API-Key`。Claude 会保存该插件设置，后续会话无需重复配置，除非密钥被修改或清除。

如果缺少密钥，或不知道去哪里获取，可通过以下方法获取秘钥：
先登录 `www.wenjuan.com`，然后进入 `个人中心 => API 对接 => MCP 对接` 复制密钥

- `WJ-API-Key`：从问卷网复制后，由 Claude 安全保存

然后按下面步骤在 Claude Code 中完成配置：

1. 运行 `/plugins`。
2. 找到 `wenjuan-survey` 插件。
3. 打开Configure options。
4. 在 `WJ-API-Key` 输入框中仅粘贴密钥本身。
5. 保存设置。
6. 如果当前会话没有自动生效，运行 `/reload-plugins`。

## 本地开发

在本地加载插件：

```bash
claude --plugin-dir wenjuan-survey-plugin(你的插件目录，根据本地进行修改)
```

## 建议的冒烟测试

- 对一个已知项目运行 `/wenjuan-survey:view-data`，确认只读的问卷网 MCP 工具可正常使用。
- 确认插件可以成功访问项目列表、项目结构或概览数据。

## 说明

- `.claude-plugin/plugin.json` 存放插件元数据和用户配置 schema。
- `.mcp.json` 位于插件根目录，符合 Claude 插件约定。
- 该插件仅引用插件目录内部的文件，以兼容 Claude 的插件缓存行为。
