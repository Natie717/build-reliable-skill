# Build Reliable Skill

把真实、可重复、可验证的经验、流程或判断，设计成边界清楚、结构最小充分、能够被测试的候选 Skill。

> 当前版本：`v0.1.0-beta.1` 公开测试版。安装与发现已经在 Codex 和 Claude Code 环境中做过本地验证；跨用户、跨模型的连续真实试用仍在进行中。

## 它解决什么

`build-reliable-skill` 会先判断一项能力是否真的适合做成 Skill，再按任务风险与证据完整度，逐步完成：

1. 只读检查现有能力，避免重复建设；
2. 在直接协作、临时指令、脚本、Skill、工作流和 Agent 之间分诊；
3. 从用户授权的资料、真实任务和历史修改中提取候选规则；
4. 设计最小充分的 Skill 架构；
5. 在准确授权后生成候选文件；
6. 用静态检查、行为测试、回归和真实试用验证它；
7. 将候选生成、安装发现、真实试用和正式激活分开报告。

## 它不会做什么

- 不因为用户提到 Skill 就强行创建 Skill；
- 不自动安装、覆盖、激活、发布或修改外部平台；
- 不把课程内容、AI 推测或行业常识冒充用户事实；
- 不把复杂状态、长期监听或多岗位调度硬塞进单个 Skill；
- 不把静态检查或合成测试夸大成真实可用。

## 仓库结构

```text
.
├── SKILL.md
└── references/
    ├── 01-intake-and-routing.md
    ├── 02-evidence-extraction.md
    ├── 03-architecture-and-build.md
    └── 04-evaluation-and-activation.md
```

`SKILL.md` 保存每次运行都需要的职责、边界与阶段路由；四份 references 只在进入对应阶段时加载。

## 安装

### Codex

可以在 Codex 中调用 `$skill-installer`，并要求它从以下仓库安装：

```text
https://github.com/Natie717/build-reliable-skill
```

也可以手动克隆到用户级 Skill 目录。执行前请先确认目标目录不存在，避免覆盖已有 Skill：

```bash
git clone https://github.com/Natie717/build-reliable-skill.git ~/.agents/skills/build-reliable-skill
```

### Claude Code

本项目也在 Claude Code 的用户级 Skill 发现路径中做过本地发现测试：

```bash
git clone https://github.com/Natie717/build-reliable-skill.git ~/.claude/skills/build-reliable-skill
```

不同 Claude Code 版本、模型供应方和工具环境可能存在差异。目前不把有限的本地测试宣称为完整兼容。

## 使用

显式调用示例：

```text
$build-reliable-skill
我想把自己的真实工作经验做成一个 Skill。请先判断它是否适合，并从只读分诊开始。
```

也可以直接描述需求，让支持隐式触发的宿主根据 `description` 判断是否调用。

## 当前验证状态

已验证：

- Skill 文件结构与相对链接；
- Codex 的显式调用、隐式触发和负向不触发；
- Claude Code 的显式调用、隐式触发和负向不触发；
- 多类隔离行为案例、权限门禁和回归检查。

仍需外部测试：

- 不同用户的真实连续工作流；
- 不同 Codex、Claude Code 和模型版本；
- 长期使用中的交互成本、重复提问和返工；
- 外部工具、脚本和高风险场景的边界表现。

详细测试方法见 [TESTING.md](TESTING.md)。发现问题请使用仓库的 Issue 模板；开放讨论、使用经验和方向建议请进入 Discussions。

## 隐私与安全

- 不要在公开 Issue、Discussion 或测试记录中粘贴 API Key、Cookie、密码、私人文件、客户资料或未脱敏对话；
- 提交测试记录前，请替换个人绝对路径、姓名、账号、联系方式和业务数据；
- 在真实项目中使用时，先确认允许读取和写入的准确范围；
- 任何公开、安装、覆盖、删除或外部写入都应保持独立的人类授权门禁。

## 贡献

欢迎提交真实试用报告、可复现问题、兼容性结果和改进建议。修改运行规则的 Pull Request 应说明它解决的真实问题，并附上对应测试或回归证据。详见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 来源说明

本项目部分设计思路参考了生财有术「Agent Skills 炼术营」相关课程内容，并结合维护者的真实任务、独立筛选、重写、组织与验证形成。本仓库不包含课程全文、专有案例、活动编号、内部访问记录或个人知识库内容。

本项目同时遵循开放 Agent Skills 的目录约定，并参考了 OpenAI 关于 Skill 渐进披露、发现与分发的公开文档。

## License

[Apache License 2.0](LICENSE)

---

English summary: A Chinese-first public beta skill for turning real, repeatable experience into scoped and testable Agent Skills. Cross-user and cross-model field validation is still in progress.
