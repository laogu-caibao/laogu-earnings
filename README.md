# 业绩预告解读

`laogu-earnings`

业绩预告解读 skill：按关注清单扫描近 1 个月发布的业绩预告/业绩快报，抓取正文提炼利润区间与同比口径，输出中文解读与超预期判断。

## 一键安装

```bash
npx skills add laogu-caibao/laogu-earnings
```

仓库地址（点击复制）：

`https://github.com/laogu-caibao/laogu-earnings`

**方式一：克隆**

```bash
git clone https://github.com/laogu-caibao/laogu-earnings.git
```

**方式二：下载 ZIP**

https://github.com/laogu-caibao/laogu-earnings/archive/refs/heads/main.zip

**导入使用**

- Claude Code / Muse：把仓库中的 `SKILL.md` 放到 `~/.claude/skills/laogu-earnings/` 下即可调用。
- 豆包智能体 / Workbuddy 等：按各平台的 skill 上传流程导入 `SKILL.md`。
- 扣子 Coze：扣子编程 → 技能面板 → 创建技能 → 本地上传，上传本仓库打包的 zip（仓库根目录已有 SKILL.md，直接压缩仓库文件夹即可）；如页面要求 `.skill` 后缀，由扣子导入后自动生成，不要只改扩展名。
- Trae：设置 → 技能 → 上传技能，上传同上 zip；或手动放到 `~/.trae/skills/laogu-earnings/`（项目级用 `.trae/skills/laogu-earnings/`）。Trae 也支持 MCP：把 `uvx laogu-mcp` 配进 MCP 设置即可获得 16 个工具（skill 负责流程指导、MCP 负责工具调用）。
- 一次装好全部 16 个：用 [laogu-mcp](https://github.com/laogu-caibao/laogu-mcp)，`uvx laogu-mcp` 一键安装。
## 文件结构

- `SKILL.md` — 主流程（平台中立，定时能力由宿主平台提供）
- `references/sources.md` — 数据源：东财公告列表与正文接口、一致预期搜索路径

## 输出结构

- 每家公司一条：公告标题、发布时间、预告区间、归母净利区间+中值、同比口径、业绩变动原因、超预期判断
- 窗口内无预告的公司如实说明，不编造

## 内置默认清单

贵州茅台 600519、宁德时代 300750、招商银行 600036、比亚迪 002594、中芯国际 688981（可在消息中指定任意公司覆盖；注意中芯国际为 688981，勿与 688001 华兴源创混淆）

## 定时建议

- 每周一开盘前运行一次，覆盖上周新增预告
- 可与 `laogu-announcements` 联动，共用同一关注清单

---
## English

**laogu-earnings — Earnings preview interpreter.** Scans the last month's earnings previews and flash reports, extracts profit ranges with like-for-like YoY comparison, and judges whether results beat expectations. Install: `npx skills add laogu-caibao/laogu-earnings`.

## FAQ

**Q：laogu-earnings 有什么用？**
适合的场景：业绩预告季想知道一家公司的预告利润区间、同比口径是否可比、到底算超预期还是不及预期。

**Q：数据可靠吗？会荐股吗？**
数字必须来自可核验的公开来源（上市公司公告、交易所公开数据、公开网页），取不到就标「未核验」，绝不编造；只做结构化整理与解读，不构成投资建议。

**Q：怎么安装？支持哪些 AI 平台？**
```bash
npx skills add laogu-caibao/laogu-earnings
```
平台中立 Markdown，Claude Code、Codex、豆包智能体、Workbuddy、扣子 Coze、Trae 等环境均可用；数据能力可用 [laogu-mcp](https://github.com/laogu-caibao/laogu-mcp)（`uvx laogu-mcp`）一次装齐。更多 skill 见[老谷拆财报组织主页](https://github.com/laogu-caibao)。
---

## 出品

**老谷拆财报** —— 以数据为刃，剖市场真相

- 抖音 / 微信视频号 / 今日头条 / 快手：搜索「老谷拆财报」
- 固定栏目：「价值投资之财报解读」（全网连载中）
- 本 skill 的方法论与账号内容同源：数据驱动、拆开看、不讲黑话

### 扫码关注

| 微信视频号 | 抖音 |
|---|---|
| ![视频号二维码](docs/qrcode-shipinhao.jpg) | ![抖音二维码](docs/qrcode-douyin.png) |
| 扫一扫，关注视频号 | 抖音号：gubaobao22 |

> 作者声明：个人观点，仅供参考，不构成投资建议。
