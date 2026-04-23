---
name: gudong-inbox-save
description: inBox 笔记保存工具。通过 API 将笔记保存到 inBox 应用。支持标题和内容，零配置。当用户说"保存到inBox"、"记到inBox"、"存到笔记"时触发。
---

# inBox 笔记保存

通过 inBox API 将笔记保存到云端，支持标题和内容字段。

## 触发场景

当用户提到以下需求时触发本技能：

- "保存到inBox"
- "记到inBox"
- "存到笔记"
- "inBox 记一笔"

## 使用方式

### 无标题保存

```bash
curl -s -X POST https://api.gudong.site/inbox/x4zZcOEKEUAT35LYNlAufkI12Bm0Ti \
  -H "Content-Type: application/json" \
  -d '{"content":"笔记内容"}'
```

### 有标题保存

```bash
curl -s -X POST https://api.gudong.site/inbox/x4zZcOEKEUAT35LYNlAufkI12Bm0Ti \
  -H "Content-Type: application/json" \
  -d '{"content":"笔记内容","title":"标题"}'
```

## API 说明

- **接口地址**: `https://api.gudong.site/inbox/{userToken}`
- **请求方式**: POST
- **Content-Type**: application/json

## 请求参数

| 参数 | 类型 | 是否必填 | 说明 |
|------|------|----------|------|
| content | 字符串 | 是 | 笔记内容，最多3000字符 |
| title | 字符串 | 否 | 笔记标题 |

## 限制

- 每天最多上传 50 条
- content 最多 3000 字符

## 获取 Token

1. 打开 inBox 应用
2. 首页 > 侧边菜单 > 设置 > 账户 > API
3. 复制你的专属 Token
4. 替换命令中的 `{userToken}`

## 返回结果

成功返回：

```json
{
  "code": 0,
  "msg": "success"
}
```

失败返回：

```json
{
  "code": -1,
  "msg": "错误信息"
}
```

## 不做什么

- 不编辑笔记内容
- 不提供笔记列表/搜索功能
- 不管理分类/标签
- 仅负责保存
