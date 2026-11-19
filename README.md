# drawio-skills

个人管理的 draw.io Agent Skills 聚合仓库，整合了 4 个社区 Skill 仓库的全部 7 个 Skill，并已针对官方 `jgraph/drawio-mcp`（插件/Skill/MCP 名均为 `drawio`）完成了**去冲突改名与相对路径修正**。

---

## 包含的 Skill 清单（均不与 `drawio` 冲突）

| Skill 目录 / 名称 | 来源仓库 | 定位 | 去冲突处理说明 |
| --- | --- | --- | --- |
| `skills/drawio-skill` | `Agents365-ai/drawio-skill` (v3.4.4) | 架构图、16 种代码/IaC/Schema 导入、10k+ 官方图标、321 AI Logo、自检闭环 | 原名已无冲突；保留 `disable-model-invocation: true`（仅显式调用，不抢触发） |
| `skills/drawio-yaml` | `bahayonghang/drawio-skills` (`skills/drawio`, v2.8.0) | 离线 YAML-first 工作流（7 主题、15 色板、309 离线图标） | **原名 `drawio` 已改名为 `drawio-yaml`**；已删除其内置的 `.mcp.json`（原定义同名 `drawio` MCP Server） |
| `skills/drawio-academic-skills` | `bahayonghang/drawio-skills` (`skills/drawio-academic-skills`, v2.8.0) | IEEE/ACM/Nature/学位论文投稿前检查学术扩展层 | 所有同级依赖引用 `../drawio` / `skills/drawio` 已全部修正为 `../drawio-yaml` / `skills/drawio-yaml`（**必须与 `drawio-yaml` 同级安装**） |
| `skills/drawio-diagram-builder` | `Will-hxw/drawio-diagram-builder` (v0.4.1) | 顶会论文方法图与截图驱动参考图复刻 | 原名已无冲突 |
| `skills/research-draw` | `QIANJINYDX/research-drawio-skill` | 两阶段科研图（先参考图再临摹为 `.drawio`） | 原名已无冲突；与 `draw-science` / `add-svg` 配套使用 |
| `skills/draw-science` | `QIANJINYDX/research-drawio-skill` | 科研流程图、机制图、MathJax 与 QA 校验脚本 | 原名已无冲突 |
| `skills/add-svg` | `QIANJINYDX/research-drawio-skill` | 科研矢量 SVG 图元检索/自绘与集成 | 原名已无冲突 |

---

## 安装方式（可与 `jgraph/drawio-mcp` 共存）

### 1. Claude Code（按需挑模块装，推荐）
仓库根目录自带 `.claude-plugin/marketplace.json`（市场名 `chan-yuu-drawio-skills`，不与官方 `@drawio` 冲突），拆分为 4 个独立插件，可按需装删：

```text
/plugin marketplace add chan-yuu/drawio-skills

# 按需选择安装（可全装或只装需要的组）
/plugin install drawio-arch@chan-yuu-drawio-skills        # Agents365-ai (drawio-skill)
/plugin install drawio-yaml-suite@chan-yuu-drawio-skills  # bahayonghang (drawio-yaml + drawio-academic-skills)
/plugin install drawio-builder@chan-yuu-drawio-skills     # Will-hxw (drawio-diagram-builder)
/plugin install drawio-research@chan-yuu-drawio-skills    # QIANJINYDX (research-draw + draw-science + add-svg)
```

### 2. Codex CLI
仓库根目录自带 `.agents/plugins/marketplace.json` 与 `.codex-plugin/plugin.json`（市场名 `chan-yuu-drawio-skills`，插件名 `drawio-skills-suite`，不与官方 `drawio@drawio` 冲突）：

```bash
codex plugin marketplace add chan-yuu/drawio-skills
codex plugin add drawio-skills-suite@chan-yuu-drawio-skills
```

### 3. `npx skills` 或手动安装单个 Skill
```bash
# 交互式选择要安装的 Skill
npx skills add chan-yuu/drawio-skills

# 或克隆后手动复制所需子目录到 ~/.claude/skills/ 或 ~/.codex/skills/
# 注意：安装 drawio-academic-skills 时必须同时复制同级的 drawio-yaml
```

---

## 上游来源与许可说明

* `Agents365-ai/drawio-skill` — MIT（见 `UPSTREAM_LICENSES/LICENSE-Agents365-ai-drawio-skill.txt`）
* `bahayonghang/drawio-skills` — MIT（见 `UPSTREAM_LICENSES/LICENSE-bahayonghang-drawio-skills.txt`）
* `Will-hxw/drawio-diagram-builder` — MIT（见 `UPSTREAM_LICENSES/LICENSE-Will-hxw-drawio-diagram-builder.txt`）
* `QIANJINYDX/research-drawio-skill` — 上游仓库未声明开源协议（仅作个人学习与归档引用，请勿商用）
