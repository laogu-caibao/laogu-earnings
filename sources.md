# 数据源（2026-09-29 实测修订）

## 公告列表（东方财富，实测最稳）

- 公告列表接口：`https://np-anotice-stock.eastmoney.com/api/security/ann?cb=...&sr=-1&...&stock_list=CODE&...`
  - `stock_list` 用**纯数字代码**（如 `600519`），不带 `.SZ`/`.SH` 后缀
  - 带桌面端 UA 请求；返回 JSON，公告的 `art_code`（AN+日期前缀，字典序即时间序）、标题、`notice_date`（带毫秒，精确到秒截断）、`columns[].column_name`（官方栏目分类）、原文链接拼法：`https://data.eastmoney.com/notices/detail/CODE/ART_CODE.html`
  - 筛选：`column_name` 含"业绩预告"直接命中；再用标题关键词（"业绩预告"、"业绩快报"）复核补漏
  - **代码核验**：用返回的 `codes[].short_name` 与目标公司简称交叉核对，防止代码串码（实测教训：中芯国际是 688981，688001 是华兴源创）

## 公告正文（东财正文接口）

- 正文接口：`https://np-cnotice-stock.eastmoney.com/api/content/ann?art_code={art_code}&client_source=web&page_index=1`
  - 请求头带 `Referer: https://data.eastmoney.com/`
  - 成功标志：返回 JSON `success==1`；正文在 `data.notice_content`（含 HTML 标签，需 strip）
  - 判定失败：`success!=1` 或 `notice_content` 为空 → 降级为"标题归纳 + 原文链接"，数字项标注"未核验"
  - **不要用 curl 去抓 `data.eastmoney.com/notices/detail/...` 页面**：那是 JS 重度渲染的空壳页，正文不在 HTML 里，只能走上面的 content API

## 一致预期（市场预期，无稳定程序化公开接口）

- 一致预期数据**没有稳定公开的程序化接口**；需要时用网页搜索：`{公司} 业绩预告 超预期 券商` 或 `{公司} 业绩预告 点评`，取研报/券商观点并注明来源
- 搜不到可用预期数据时，**不做超预期判断**，只描述预告事实（区间、中值、同比口径、变动原因）
- 备选参考：历史同期增速对比（用该公司上一年度同期财报实际数）

## 兜底规则

接口失败或数据对不上时，一律用网页搜索补足并注明来源；补不到的标注"未核验"，不编造数字。
