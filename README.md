# external-ai-skills

第三方 Agent Skills / Plugins / CLI 的**原始来源库**。

这个仓库只负责保存“外部原版”和上游同步基线，不放个人定制逻辑。个人原创和定制版本统一放在 `Guluguluxxx/my-ai-skills`。

## 与 my-ai-skills 的关系

```text
Upstream GitHub
      ↓
external-ai-skills
原始版本 / 来源 / commit 基线
      ↓
Base / New / Mine 三方比较
      ↓
my-ai-skills
个人原创 + adapted 定制版本
```

## 两种保存模式

### 1. mirror

仅用于上游有明确允许再分发的许可证。

目录中保存经过核对的**原始未修改文件**，同时记录：

- upstream repository
- upstream path
- branch / tag
- synced commit
- license
- sync date

镜像文件禁止个人修改。

### 2. pointer

用于以下情况：

- 上游没有明确 LICENSE；
- 许可证不允许直接重新分发；
- 仅需要版本基线，不需要复制源码。

pointer 模式只保存来源信息、commit、文件 SHA 和更新记录，不复制上游源码。

## 更新规则

每次检查上游更新：

1. 获取 upstream 最新 commit。
2. 对比当前 synced commit。
3. 先分析 upstream diff。
4. 更新本仓库中的原版镜像或指针基线。
5. 找到 `my-ai-skills` 中关联的 adapted Skill。
6. 做 Base / New / Mine 三方比较。
7. 报告：
   - 上游改了什么；
   - 哪些值得同步；
   - 哪些与个人定制冲突；
   - 权限、依赖、安全边界是否变化；
   - 建议合并方案。
8. 未经确认，不覆盖 `my-ai-skills` 中的个人定制 Skill。

## 目录

```text
sources/
└─ <owner>/
   └─ <repo-or-skill>/
      ├─ SOURCE.yaml
      ├─ UPSTREAM.md
      └─ upstream/        # 仅 mirror 模式存在

registry.yaml             # 所有已跟踪来源
```

## 分享原则

- 分享第三方原版：优先给 upstream GitHub；需要固定版本时可引用本仓库的 source 记录 / mirror。
- 分享个人定制版：从 `my-ai-skills` 分享，并保留 SOURCE 信息与修改说明。
- 不把 Token、Cookie、API Key、账号状态、本机路径或个人数据提交到本仓库。
