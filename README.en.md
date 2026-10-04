# Bilibili Single-Video Chapter Notes

Turn the chapters, subtitles, or summary already visible on one Bilibili video page into evidence-backed learning notes. Every delivered row points back to visible page text, a timestamp when available, and the video URL. If subtitles or a summary are not visible, the skill reports only the visible title and missing material—it never claims to have watched the video.

## Input and output

Provide a video URL, learning goal, and a user-selected Easy WebBridge `browserId`. The output is a Markdown chapter/timestamp table with notes, page evidence, collection scope, and gaps. It processes at most 100 visible rows per run.

## Install

```bash
npx skills add xxjrq/bilibili-video-chapter-notes-free
```

This browser skill requires [Easy WebBridge on GitHub](https://github.com/jackwener/Easy-WebBridge), with [Gitee as a fallback](https://gitee.com/jackwener/Easy-WebBridge). It uses only the `browserId` supplied by the user and keeps each task in its own session/tab group.

The workflow is read-only by default, does not bypass sign-in, CAPTCHA, or risk controls, and never downloads or transcribes video media. Offline fixtures and the self-test validate rendering behavior only; they are not online collection results.

```bash
bash scripts/self-test.sh
```

See [SOURCES.md](SOURCES.md) for reference attribution and [LICENSE](LICENSE) for licensing.
