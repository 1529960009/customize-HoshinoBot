# HoshinoBot (customized)

HoshinoBot的个人修改版。安装和部署指南请看[部署](#deploy)。

本项目不提供资源文件。

## 简介

本项目对原版机器人进行了少许修改，这些修改可能导致与原版机器人部分功能不兼容。修改包括：

- 在[语料库](https://github.com/iamwyh2019/custom-HoshinoBot/blob/master/hoshino/modules/groupmaster/chat.py)中加入更多应答；
- <del>在[资源库接口](https://github.com/iamwyh2019/custom-HoshinoBot/blob/master/hoshino/R.py)中添加ResRec类以处理语音；</del>这个类还在，但是cqhttpmirai暂不支持语音（embedded分支支持），所以删掉了```chat.py```里面的语音信息；
- 在[广播](https://github.com/iamwyh2019/custom-HoshinoBot/blob/master/hoshino/modules/botmanage/broadcast.py)中添加“单个群发消息”功能；
- **不兼容**：修改[每日签到](https://github.com/iamwyh2019/custom-HoshinoBot/blob/master/hoshino/modules/priconne/login_bonus.py)访问印章图片的位置，支持印章图片集的热更新；加入重置签到情况的功能。不兼容的原因是修改了印章路径；
- 在[反滥用](https://github.com/iamwyh2019/custom-HoshinoBot/blob/master/hoshino/modules/groupmaster/anti_abuse.py)中加入主动拉黑某个人或某个群（及解除拉黑）的功能；
- 增加[角色数据库](https://github.com/iamwyh2019/custom-HoshinoBot/blob/master/hoshino/modules/priconne/_pcr_data.py)中内容；**注意**：额外的资源文件并未上传；
- **不兼容**：公会战期间[hourcall](https://github.com/iamwyh2019/customize-HoshinoBot/blob/master/hoshino/modules/hourcall/hourcall.py)将使用一套专门针对公会战的文案。同时，添加了手动触发报时功能，方便调试。不兼容的原因是在文案文件中加入当期公会战的日期，在读入原版文案时会因为不存在这个信息而报错；正在思考更好的判断现在是否是公会战的方式；
- 修改[公会战管理系统](https://github.com/iamwyh2019/customize-HoshinoBot/blob/master/hoshino/modules/pcrclanbattle/clanbattle/cmdv2.py)中部分命令的参数，以更好地管理出刀记录、催刀等；

同时，编写或安装了若干插件，包括：

- 查询公会战排名；[项目地址](https://github.com/pcrbot/clanrank)
- 查询简介、技能、专武信息；[项目地址](https://github.com/pcrbot/pcr-wiki)
- 查看日程表；[项目地址](https://github.com/pcrbot/schedule)
- 通过网页管理服务；这个插件的```view.py```由于含有密码而没有上传；
- 群空调；
- 表情生成器；
- 公会战离职报告；

这些插件的著作权属于原作者，均按GPL-v3协议开源。

除此之外，本项目增加了部分参数的修改接口，实现参数热更新，包括：

- 重置每日签到情况
- 更新印章库里的印章列表
- 设置查询拆法时显示的最大作业数

具体的更新内容可查阅commit与更新日志<del>（近期上线）</del>（不想写了）

## 开源

本项目按GPL-v3协议开源。您可以任意复制、使用、修改、署名该作品及衍生作品，但若要向非开发者分发这些作品，则需要以GPL-v3协议开源。详情请阅读[开源协议](https://github.com/iamwyh2019/custom-HoshinoBot/blob/master/LICENSE)。

<h2 id="deploy"> 部署 </h2>

**注意**：本项目代码与使用中的机器人代码实时同步更新，但出于隐私原因，所有配置文件都不会公开。这可能导致部署困难。因此，我们建议您不直接使用本项目代码。

由于酷Q框架停止服务，本项目已迁移至mirai框架上。请确保您的电脑上安装有jre8及python3.8或更高版本。首先，参考HoshinoBot的[项目地址](https://github.com/Ice-Cirno/HoshinoBot)中“部署指南”一章，下载机器人代码并填写配置信息；随后，参考mirai部署教程（[Windows](https://yobot.win/install/Windows-cqhttp-mirai.html)或[Linux](https://yobot.win/install/Linux-cqhttp-mirai.html)）中“部署mirai”一章，下载并配置miraiOK与cqhttp-mirai。注意HoshinoBot与mirai的配置文件中，反向代理的IP及端口应保持一致。配置完后，依次启动HoshinoBot与miraiOK，向机器人发送“在吗”测试，若有回复则部署成功。