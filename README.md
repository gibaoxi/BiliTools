[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/catlair/BiliTools/blob/main/LICENSE)
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/catlair/BiliTools)](https://github.com/catlair/BiliTools/releases)
[![欢迎 PRs](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/catlair/BiliTools/pulls)
[![GitHub issues](https://img.shields.io/github/issues/catlair/BiliTools)](https://github.com/catlair/BiliTools/issues)
![Docker Image Size (latest by date)](https://img.shields.io/docker/image-size/catlair/bilitools)
![Docker Pulls](https://img.shields.io/docker/pulls/catlair/bilitools)
![Lines of code](https://img.shields.io/tokei/lines/github/catlair/BiliTools)
![GitHub release (latest by date)](https://img.shields.io/github/downloads/catlair/BiliTools/total)

## 支持功能

- [x] 部分方式每日随机时间运行
- [x] 每日签到/分享/播放
- [x] 直播签到
- [x] 漫画签到
- [x] 每日自动投币（指定数量）
- [x] 银瓜子兑换硬币
- [x] 硬币赛事竞猜（不保证胜率，支持正压、反压和随机压）
- [x] 直播间弹幕（每日首次获得 100 亲密度，自动点亮灰色勋章）
- [x] 领取年度大会员权益/B 币券（无测试条件，待测试）
- [x] 自动使用 B 币券充电
- [x] 直播赠送即将过期的礼物（为确保安全，只赠送辣条和小心心）
- [x] 多账号独立配置
- [ ] 直播天选时刻（测试）
- [ ] 直播礼物红包（测试）
- [ ] 支持 Docker 、腾讯 SCF 、阿里 FC、百度 CFC、华为 FG、青龙面板等方式运行，支持执行消息推送
- [ ] 代码自动在线更新，发包任你发
- [x] ~~直播挂机获取小心心~~
- [x] ~~应援团签到~~
- [ ] ~~风纪委员 headless 版（不支持 scf）见 [bili-task-puppeteer](https://github.com/catlair/bili-task-puppeteer)~~（没有资格）

## 使用说明

消息推送直接使用了 `青龙面板` 中的消息推送

### 重要提示

SCF 将在 6.1 正式取消免费额度，如有需要请停止使用 SCF。[点击链接](https://cloud.tencent.com/act/pro/web_function?from=15018)购买 1 元年包（可购买两次，时间不可叠加）

新增天选时刻 [天选时刻任务配置](./docs/readme.md#天选时刻任务配置)

直播获取小心心改版，暂时关闭相关功能。

支持获取在线代码运行，部署一次即可长期更新（逻辑不变的情况下），添加环境变量 `USE_NETWORK_CODE` 尝试，百度云不支持环境变量，可以在附加消息中添加 `USE_NETWORK_CODE` 字段。值为字符串，可以是任意值，但不能为空。

## 使用方法

详细文档查看 [docs 目录](./docs)  
**若 Github 无法查看图片，请访问 [Gitee](https://gitee.com/catlair/BiliTools/tree/main/docs)**

使用必读：

- [Cookies/UA 获取方法/配置详情](./docs)
- [参考配置](./config/config.example.json5)

运行方法：

- [腾讯 SCF（无免费额度）](./docs/手动部署到SCF.md)：想白嫖？没门。
- [阿里 FC](./docs/手动部署到FC.md)：除了文档奇烂，其它都挺好，暂时有免费的额度。
- [百度 CFC](./docs/手动部署到CFC.md)：功能欠缺，编辑器只能看到入口文件，但是每日任务足够了。
- [华为 FG](./docs/手动部署到FG.md)：网页交互极差，错误提示不明显甚至没有，没有 loading 效果，偶尔发生无法跳转。
- [华为 AGC-FC](./docs/手动部署到AGC-FC.md)：功能欠缺，上传代码无法看到入口文件。页面交互体验比自家云函数好。
- ~~[Action 部署到 SCF](./docs/Action部署到SCF.md)~~（使用量一直为 0，再加上收费的原因，取消该方法）
- [使用 Docker 运行](./docs/使用Docker运行.md)
- [本地运行](./docs/本地运行.md)
- [gzip 在线压缩](https://www.baidufe.com/fehelper/en-decode/index.html)
- [青龙面板](./docs/%E9%9D%92%E9%BE%99%E9%9D%A2%E6%9D%BF.md): 自行添加 Node 依赖 `axios`, 自行创建 `cat_bili_ql.json5` 文件（脚本管理中）。参考 [#46](https://github.com/catlair/BiliTools/issues/49)。
- [已编译文件下载](./docs/%E7%BC%96%E8%AF%91%E6%96%87%E4%BB%B6%E4%BB%8B%E7%BB%8D.md)

视频参考：

https://www.aliyundrive.com/s/MBZ45dkeMnp

### npm 包

做为全局命令使用

```bash
npm install -g @catlair/bilitools
bilitools -h
bilitools -c ./config.json
```

做为模块使用

```javascript
// scf
exports.main_handler = require('@catlair/bilitools').scf_handler();
// 本地
const bilitools = require('@catlair/bilitools');
bilitools.run();
```

### Docker 镜像

- ~~`catlair/bilitools-deploy` 用于部署到 SCF~~
- `catlair/bilitools` 用于直接运行

## 参考项目

- [SocialSisterYi/bilibili-API-collect](https://github.com/SocialSisterYi/bilibili-API-collect)
- [catlair/bili-task-puppeteer](https://github.com/catlair/bili-task-puppeteer)
- [lzghzr/TampermonkeyJS](https://github.com/lzghzr/TampermonkeyJS)
- [whyour/qinglong](https://github.com/whyour/qinglong)
- [RayWangQvQ/BiliBiliToolPro](https://github.com/RayWangQvQ/BiliBiliToolPro) （推荐转用）

## 责任声明

1. bug 是不可避免的，我们尽量减少 bug 所带来得损失，**但这并不意味着我们要为此负责**，选择权在您，望周知。
2. 不会以任何方式收集用户 mid、Cookies、关注列表、收藏记录等信息。项目只向 B 站提供 Cookies，请不要将 Cookies 上传到 Github 等**开放平台**以及其他任何**不可信**平台。
3. 仓库中内置的任何 B 站相关用户信息，都不会影响你的投币、充电、打赏，权利掌握在使用者手中。
4. 如果您有任何疑问，请提交 issue，我们会尽快给予回复。
