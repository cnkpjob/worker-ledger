# 打工人小账本（GitHub 版）

把「工时」和「花钱」放在一起看的个人记账工作台。奶油薄荷手账风，桌面侧栏 / 手机底部 Tab。

> 数据真正存在**线上**，不是浏览器本地：本仓库 `data/` 下的三个 JSON 文件就是数据库，页面通过 GitHub REST API 直接读写，换设备 / 换浏览器登录同一账号即可同步。

## 功能
- 真实时薪计算器（展开完整公式：名义时薪、年投入工时、真实时薪）
- 10 秒记账（金额 / 分类 / 备注，保存即换算成工作时间）
- 首页最近 4 笔、今日 / 本月支出
- 月度收入与固定 / 弹性支出总结（自动结余）
- 自由基金目标进度与安全垫
- 原生 SVG 存款曲线
- 通勤 / 加班 / 涨薪三情景模拟

## 部署（GitHub Pages）
1. 把本仓库 fork 或上传到你的 GitHub 账号（保持 `index.html` 在根目录、`data/` 目录结构不变）。
2. 仓库 **Settings → Pages → Build and deployment → Source：Deploy from a branch → 选 `main` 分支、目录 `/(root)`**，保存。
3. 几分钟后访问 `https://<你的用户名>.github.io/<仓库名>/`。

## 开启云端同步（重要）
GitHub Pages 是静态站点，**页面本身公开**。数据读写需要你自己的 GitHub Token：
1. 打开 **GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**。
2. 权限只给这个仓库的 **Contents: Read and write**（更细的：Repository contents → Read and write）。
3. 仓库里打开页面，首页底部「☁️ 云端同步设置」填：仓库 `owner/repo`、分支 `main`、Token。点「保存并连接」。
4. Token 只存在你本机浏览器 `localStorage`，不会上传到任何第三方。

## 隐私提醒
- Pages 站点地址是**公开的**，而数据文件在你的仓库里：若仓库为 **Public**，懂行的人能直接读 `data/*.json` 看到你的账目。
- 想要账目不被外人看到：把仓库设为 **Private**（GitHub Pages 仍可用，但站点本身仍对外可访问）；或仅把本仓库当作「演示 / 公开账本」，真实私密数据用「资料库」版本。

## 数据结构
- `data/txns.json` → 流水记录
- `data/settings.json` → 个人设置（时薪参数、自由基金目标等，单行）
- `data/monthly.json` → 月度账页（逐月总结）
