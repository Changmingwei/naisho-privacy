# naisho-privacy → naisho.space 的站点

这个仓库原来只放隐私政策一页，2026-09-07 起变成 **naisho.space 整个站点**的源码。
托管走 **Cloudflare Pages**（连的就是这个仓库，`main` 分支，构建输出目录 `/`），
域名 `naisho.space`。全站是静态文件，没有构建步骤，**一行第三方脚本都没有**。

## 现在有什么

| 路径 | 是什么 | 状态 |
|---|---|---|
| `/index.html` | **暂时还是隐私政策**——这个地址（`https://changmingwei.github.io/naisho-privacy/`）已经填进 App Store Connect 两处，**在 ASC 改掉之前一个字节都不能动** | 上线中 |
| `/privacy/` | 同一份隐私政策，站点改版后的正式位置 | 已就位 |
| `/support/` | 支持页（App Store 的支持 URL 会指这里） | 待做 |
| `/` 首页 | 产品介绍页 | 待做（设计中） |
| `_headers` `_redirects` `robots.txt` | Cloudflare Pages 的配置 | 已就位 |

## 改版分两段，顺序不能反

App Store 审核会去抓 ASC 里填的那两个隐私政策 URL。**任何时候都不许出现 404。**

1. **第一段（已完成）**：新增 `/privacy/`，根上那份不动。老地址、新地址同时活着，内容一样。
2. **第二段（等域名和 Pages 都好了）**：改 ASC 里那两处 URL 指向 `https://naisho.space/privacy/`，
   **确认新地址返回 200 之后**，再把根上那份换成介绍页。

## 记录源在哪

隐私政策的**正文记录源是私有仓库 `Changmingwei/AirBuddy` 的 `docs/privacy-policy.md`**。
改了 app 的数据行为（尤其是诊断上传），要三处一起改：那份 markdown、这里的 `/privacy/`、
以及 App Store Connect 的 App 隐私问卷。

整件事的来龙去脉、以及只有域名持有人能点的那几步，写在 `AirBuddy/docs/naisho-space.md`。

## 改了怎么上线

推到 `main`，Cloudflare Pages 自己部署。**和 app 出包完全无关**——不占 TestFlight 的上传配额，
也不受 `Scripts/cadence.py` 那套合版节奏管。
