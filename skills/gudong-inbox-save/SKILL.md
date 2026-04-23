---
name: gudong-inbox-save
description: inBox 笔记保存工具。通过 API 将笔记保存到 inBox 应用。支持标题和内容，零配置。当用户说"保存到inBox"、"记到inBox"、"存到笔记"时触发。
env:
  INBOX_TOKEN: "inBox API Token（在设置 > 账户 > API 中获取）"
---

# inBox 笔记保存

通过 inBox API 将笔记保存到云端，支持标题和内容字段。

## 触发场景

- "保存到inBox"
- "记到inBox"
- "存到笔记"

## 配置

使用前需要设置环境变量：

```bash
export INBOX_TOKEN="your_token_here"
```

或添加到 `~/.zshrc`：

```bash
echo 'export INBOX_TOKEN="your_token_here"' >> ~/.zshrc
source ~/.zshrc
```

## 获取 Token

1. 打开 inBox 应用
2. 首页 > 侧边菜单 > 设置 > 账户 > API
3. 复制你的专属 Token

## 使用方式

### 无标题保存

```bash
curl -s -X POST "https://api.gudong.site/inbox/${INBOX_TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{"content":"笔记内容"}'
```

### 有标题保存

```bash
curl -s -X POST "https://api.gudong.site/inbox/${INBOX_TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{"content":"笔记内容","title":"标题"}'
```

## 限制

- 每天最多上传 50 条
- content 最多 3000 字符
