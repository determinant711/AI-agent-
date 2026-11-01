# Python → AI Agent 学习记录

目标：从 Python 基础走到能面试、能交付的 **AI Agent 开发工程师**。

- 默认周期：16 周
- 每天：3–5 题，60–90 分钟
- 复盘：每 14 天一份阶段报告
- 教练：`python-ai-agent-coach` skill（见上级目录 `.dsh/skills/`）

## 当前状态

- 首次配置：未完成
- 当前 Day：0
- 最近报告：—

## 目录

```text
progress/
├── profile.md       # 学习者配置（唯一配置源）
├── mastery.md       # 8 维能力等级
├── mistakes.md      # 错题账本
├── index.md         # 每日索引
├── daily/           # 每日题目 + 作答 + 解析
├── reports/         # 双周报告
└── sync-status.md   # 最近一次 Git 同步状态
projects/            # 项目里程碑
notes/               # 自由笔记
.coach/              # 本地私有答案键，不提交
```

## 每日流程

1. 教练读取档案、到期错题、最近记录。
2. 出 3–5 题，由易到难，标 `[重点]`、`[高频]`、`[易错]`、`[岗位相关]`。
3. 你作答；不会可以先要提示。
4. 教练逐题批改、给详细解析、指出踩坑并记录。
5. 更新 `daily`、`mistakes`、`mastery`、`index`。
6. 提交并推送到 GitHub；失败会如实说明。

## GitHub 首次绑定

在 GitHub 新建一个空仓库（建议 private），然后在本目录执行：

```bash
git init -b main
git remote add origin <你的仓库 URL>
git add .
git commit -m "chore(setup): 初始化学习仓库"
git push -u origin main
```

认证建议用 `gh auth login` 或 SSH，不要把 token 写进 URL。

## 隐私

- `.coach/` 是私有答案键，已在 `.gitignore` 中忽略。
- 不要提交 `.env`、token、公司内部资料、客户数据。
- 公开仓库前请检查 daily 中的个人反思内容。
