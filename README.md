# 轻工具站 · 三站合一部署包（GitHub Pages）

纯静态站点，零依赖、零服务器成本，可部署到 GitHub Pages 免费托管。

## 站点结构

| 路径 | 内容 | 更新方式 |
|---|---|---|
| `/` | 轻工具首页（图片压缩 / 二维码 / 文案生成） | 静态，可随时人工替换 |
| `/kb/` | AI 办公效率知识库（原创实操教程文章） | 每日 23:30 由定时任务「知识库站日更」写入 `kb/articles.json` + 文章页 |
| `/shop/` | AI 办公效率产品店（数字商品落地页） | 每周日 22:30 由定时任务「数字产品店周更」写入 `shop/products.json` + 产品页 |

## 数据联动约定（重要）

- `kb/articles.json` 与 `shop/products.json` 是站点列表的数据源，定时任务产出文章/产品页后，**同时**将条目追加写入对应 JSON，访问 `/kb/`、`/shop/` 即自动展示列表。
- 文章页命名建议：`kb/article-YYYYMMDD.html`；产品页命名建议：`shop/product-<slug>.html`。

## 变现方式（仅自助广告位 + 第三方交易）

- 三站均内置 `广告位` 区块（自助广告位，按周/月向广告主收费），无联盟广告、无追踪代码。
- 产品店商品购买链接（`products.json` 中 `url` 字段）指向第三方平台（如闲鱼商品链接），不接自主支付。
- 各页广告位联系方式邮箱为占位符 `tools-ad@example.com`，上线后需替换为真实联系邮箱。

## 部署步骤（GitHub Pages）

1. GitHub 新建仓库（公开，如 `light-tools`）；
2. 将本目录全部文件推送到仓库 `main` 分支；
3. 仓库 Settings → Pages → Source 选 `Deploy from a branch` → `main` / `/(root)` → Save；
4. 等待 1-2 分钟，访问 `https://<用户名>.github.io/light-tools/`（若仓库名为 `<用户名>.github.io` 则访问根路径）。

## 本地预览

```bash
cd deploy
python -m http.server 8080
# 打开 http://localhost:8080
```