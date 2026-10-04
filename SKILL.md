---
name: bilibili-video-chapter-notes-free
description: 使用用户指定的 B 站视频 URL、学习目标与 Easy WebBridge browserId，从网页当前可见的标题、章节和字幕整理可定位的章节笔记。适合学习复盘与资料归档；看不到字幕或摘要时仅交付可见标题、来源和缺项，不声称已看完或转录视频。
---

# B站单视频章节笔记

将一条 B 站视频页面**当前可见**的章节、字幕与摘要，转成围绕学习目标的结构化笔记和可回到页面核对的证据。它不是下载、转录或全片理解服务。

## 输入

- `videoUrl`：单个 B 站视频 URL。
- `learningGoal`：想从视频中学到或核对的主题。
- `browserId`：用户指定的 Easy WebBridge 浏览器环境。
- 可选 `draftTarget`：仅在用户明确授权时填写草稿区；默认只读。

## 输出

- 按可见章节标题或字幕时间排序的笔记；每条附页面可见文字、时间戳（若有）和 `videoUrl` 证据。
- 可见标题、UP 主/页面元数据（若有）、采集范围和缺项。
- 当没有可见字幕、章节或摘要时，输出“未见可用字幕/摘要”，只列可见标题与缺项；绝不说已看完视频。

## 执行边界

1. 先确认 URL、目标和 `browserId` 都由用户提供。安装 Easy WebBridge 后，使用其 CLI：`/path/to/easy-webbridge/cli/easy-webbridge.mjs`；先运行该 CLI 的 `--help`，再按其实际命令创建**本任务专属** session/标签组。
2. 只选择给定 `browserId`，绝不广播到全部账号或浏览器。先快照并显式使用 `--text-mode page`；每次点击、翻页或展开后及时刷新 refs。仅读取网页可见内容。
3. 不接管用户已有页面。关闭前核对 session 和标签组确属本任务创建，才可关闭；否则保留。
4. 登录、验证码、风控、权限提示或页面不可见时暂停并报告，绝不绕过。默认只读；获准填写草稿时也绝不点击最终发布、发送或提交。
5. 单次最多处理 100 行章节/字幕。超过时说明范围并请求分批；不能以未读取内容补全笔记。

## 交付格式

```markdown
# 《可见标题》章节笔记

学习目标：…
采集范围：页面当前可见的章节/字幕；未读取视频音画面。

| 时间/章节 | 笔记 | 可定位证据 |
| --- | --- | --- |
| 00:42 / 概念 | … | 页面可见章节“概念”；<videoUrl> |

缺项：未见可见字幕；未展开的章节内容未采集。
```

## 依赖与来源

这是浏览器类 Skill，需先安装 Easy WebBridge：GitHub 主下载地址 <https://github.com/jackwener/Easy-WebBridge>，Gitee 备用地址 <https://gitee.com/jackwener/Easy-WebBridge>。仅使用用户指定的环境。

业务用途参考：[OpenCLI](https://github.com/jackwener/OpenCLI) 的 B 站浏览器适配说明；本 Skill 的流程、示例和代码为原创，未复制其源码或文案。详见 `SOURCES.md`。
