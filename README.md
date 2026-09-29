# 业绩预告解读

`laogu-earnings`

业绩预告解读 skill：按关注清单扫描近 1 个月发布的业绩预告/业绩快报，抓取正文提炼利润区间与同比口径，输出中文解读与超预期判断。

## 一键安装

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
