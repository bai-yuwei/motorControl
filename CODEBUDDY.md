# dc-servo-lab — 项目规范入口（AI 协作必读）

有刷直流伺服项目：先仿真（Python 宿主 + 纯 C 控制内核），后移植（STM32F103 + i.MX6ULL）。
三个唯一事实源：路线图进度 → `README.md`；架构与目录树 → `docs/common/architecture.md`；设计决策 → `docs/common/design_decisions.md`。

## 硬性约束

1. **目录结构**：顶层仅 `docs/`（文档）、`sims/`（仿真）、`firmware/`（嵌入式代码）与根级 `README.md`、`.gitignore`、`requirements.txt`；docs/ 与 sims/ 的二级布局由 D12 定稿（docs: common/sim/hardware；sims: plant/host/tests/params）。
   - 新增/移动任何文件必须按 `.codebuddy/rules/repo-structure/RULE.mdc` 的归位表存放，禁止放置于规范外位置。
   - **禁止随意创建目录**：任何目录的新增/重命名/移动/删除都必须同步更新全部规范（决策清单、architecture.md §6、README、归位规则，见 `.codebuddy/rules/dir-sync/RULE.mdc`），经用户确认后才能落目录。
2. **语言**：任何文档、代码注释、提交信息一律简体中文（细则见 `.codebuddy/rules/docs-language/RULE.mdc`）。
3. **决策先行**：接口/结构/协议等变更先写入 `docs/common/design_decisions.md`（含理由与被拒备选），经用户确认后再实现。
4. **完成才勾选**：README 路线图状态仅在步骤交付物全部落地并同步文档后回写 ✅。

## 规则索引（.codebuddy/rules/，新建或修改后需新会话生效）

| 规则 | 加载方式 | 内容 |
|---|---|---|
| `repo-structure/RULE.mdc` | 始终生效 | 顶层结构与文件归位硬约束、新增目录登记流程 |
| `docs-language/RULE.mdc` | 始终生效 | 文档语言规范：任何文档一律简体中文 |
| `coding-standards/RULE.mdc` | 智能体请求 | C/Python 编码、注释、参数文件与提交规范 |
| `decision-memory/RULE.mdc` | 智能体请求 | 决策记录流程、记忆分工、步骤收口检查单 |
| `dir-sync/RULE.mdc` | 智能体请求 | 目录修改必须同步更新全部规范文档 |

## 当前状态备忘

- 步骤①已定稿（commit `4be9c88`）：顶层三目录 + 决策 D11。
- 任务②进行中：D12 二级目录布局已定稿（docs: common/sim/hardware；sims: plant/host/tests/params）；步骤②子任务管理见 `docs/sim/plan_step2.md`；对象模型方程决策（子子任务 2.2）待新对话专门规划。
- 阶段一 Python 依赖入口：根级 `requirements.txt`（Python 3.11+，Windows 原生）。
