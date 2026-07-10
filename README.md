# BiRelayBot

<p align="center">
  <strong>基于 Go 开发的 Telegram 双向客服机器人</strong>
</p>

<p align="center">
  用户私聊机器人 · 群组话题工作台 · 双向消息转发 · 用户管理 · 文案转发 · 批量群发
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Go-1.24+-00ADD8?style=flat-square&logo=go&logoColor=white" alt="Go">
  <img src="https://img.shields.io/badge/Telegram-Bot-26A5E4?style=flat-square&logo=telegram&logoColor=white" alt="Telegram Bot">
  <img src="https://img.shields.io/badge/PostgreSQL-14+-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL">
  <img src="https://img.shields.io/badge/Redis-6+-DC382D?style=flat-square&logo=redis&logoColor=white" alt="Redis">
  <img src="https://img.shields.io/badge/Platform-Linux-FCC624?style=flat-square&logo=linux&logoColor=black" alt="Linux">
  <img src="https://img.shields.io/badge/License-Proprietary-red?style=flat-square" alt="Proprietary License">
  <img src="https://img.shields.io/badge/Source-Private-black?style=flat-square&logo=github" alt="Private Source">
</p>

---

## 项目介绍

`BiRelayBot` 是一个使用 Go 开发的 Telegram 双向客服机器人。

用户通过私聊机器人发送消息后，机器人会在指定的 Telegram 超级群组中，为该用户创建一个独立的话题会话。

客服直接在群组话题中回复消息，机器人会自动将消息发送给对应用户，实现用户与客服之间的双向通信。

每位用户对应一个独立话题，不同用户的消息互不干扰。客服无需登录额外的网页后台，即可直接使用 Telegram 群组作为客服工作台。

> 本项目为私有专有软件，不属于开源项目。

---

## 核心功能

### 双向消息转发

用户私聊机器人发送消息后，消息会自动同步到客服群组对应的话题中。

客服在该话题内发送消息，机器人会自动将消息发送给对应用户。

支持常见 Telegram 消息类型：

- 文本消息
- 图片
- 视频
- 文件
- 动画
- 语音
- 音频
- 贴纸
- 联系人
- 位置信息
- 回复消息
- 格式化文本
- Telegram 自定义表情

---

### 群组话题工作台

机器人使用开启话题功能的 Telegram 超级群组作为客服工作台。

用户首次联系机器人时，系统会自动：

1. 保存用户基本资料
2. 创建用户会话记录
3. 在客服群组中创建独立话题
4. 建立用户与话题的绑定关系
5. 将用户消息转发到对应话题

客服只需要进入对应话题，即可直接回复用户。

---

### 用户拉黑

管理员可以在用户会话中将指定用户加入黑名单。

用户被拉黑后：

- 用户消息不再转发到客服群组
- 用户无法继续联系客服
- 用户资料和历史数据仍然保留
- 管理员可以随时解除拉黑状态

---

### 清空聊天

支持清空指定用户的聊天记录和群组话题消息。

清空操作不会影响：

- 用户基本资料
- 用户统计数据
- 黑名单状态
- 其他用户的会话
- 系统配置数据

清空后可以继续在原话题中接待用户，也可以根据程序逻辑重新创建会话。

---

### 用户统计

管理员可以查看机器人用户和消息统计数据。

统计内容包括：

- 用户总数
- 今日新增用户
- 昨日新增用户
- 正常用户数量
- 黑名单用户数量
- 当前会话数量
- 今日接收消息数量
- 今日发送消息数量
- 累计接收消息数量
- 累计发送消息数量

---

### 文案转发

管理员可以将群组中的指定文案或消息快速发送给用户。

适用于：

- 客服快捷回复
- 常见问题回复
- 活动通知
- 支付说明
- 使用教程
- 售后说明
- 风险提示
- 联系方式

支持转发：

- 普通文本
- 格式化文本
- 图片文案
- 视频文案
- 文件文案
- Telegram 自定义表情
- 消息按钮

---

### 用户群发

管理员可以向机器人用户批量发送消息。

支持群发：

- 文本
- 图片
- 视频
- 文件
- 动画
- 图文消息
- 格式化文本
- Telegram 自定义表情

群发任务可以统计：

- 目标用户数量
- 已发送数量
- 发送成功数量
- 发送失败数量
- 用户屏蔽机器人数量
- 黑名单用户数量
- 当前发送进度

> 群发时应设置合理的发送间隔，避免触发 Telegram Bot API 频率限制。

---

## 项目截图



### 客服工作台

客服群组使用 Telegram 话题模式，每位用户拥有一个独立会话话题。

<p align="center">
  <img src="https://github.com/user-attachments/assets/91f8525f-e939-4b71-ba6c-0762b4b76efb" alt="客服工作台截图" width="760">
</p>

---

### 程序控制台
<p align="center">
  <img src="https://github.com/user-attachments/assets/d88d6fe6-c6f5-4575-93f7-34a15d392804" alt="程序控制台截图" width="760">
</p>

---


## Telegram 准备工作

### 创建机器人

在 Telegram 中打开：

```text
@BotFather
```

发送：

```text
/newbot
```

按照提示创建机器人，并保存生成的 Bot Token。

---

### 创建客服群组

1. 创建一个 Telegram 群组
2. 将群组升级为超级群组
3. 开启群组话题功能
4. 将机器人添加到群组
5. 将机器人设置为群组管理员

建议授予机器人以下权限：

- 发送消息
- 删除消息
- 管理话题
- 编辑话题
- 关闭话题
- 重新打开话题
- 置顶消息

---
---

<p align="center">
  <strong>BiRelayBot</strong>
</p>

<p align="center">
  Telegram 双向客服机器人
</p>

<p align="center">
  Copyright © 2026 BiRelayBot. All Rights Reserved.
</p>
