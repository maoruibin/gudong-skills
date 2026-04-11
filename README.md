# gudong-skills

个人 Claude Code 技能合集，收集日常高频工具，开箱即用。

## 技能列表

| 技能 | 说明 | 触发方式 |
|------|------|----------|
| [gudong-tmpimg](skills/gudong-tmpimg) | 临时图床上传，默认 30 天过期，获取公开链接 | "临时上传"、"tmp upload" |
| [gudong-beautify-shot](skills/gudong-beautify-shot) | 截图美化，添加渐变背景和圆角 | "美化"、"美化一下"、"加个背景" |

### gudong-tmpimg

上传图片到临时图床 (imgland.net)，零配置，获取公开访问链接。

```bash
bash scripts/upload.sh ~/Desktop/screenshot.png
bash scripts/upload.sh ~/photo.png 7d   # 自定义过期时间
```

依赖：curl、jq

### gudong-beautify-shot

给截图添加蜜桃橙粉渐变背景 + 圆角，支持底部加文字描述。

```bash
python3 beautify.py input.png
python3 beautify.py input.png -t "这是我的截图"
```

依赖：Pillow (`pip install Pillow`)

## 安装使用

通过软链接将技能目录链接到 Claude Code 的 skills 目录：

```bash
ln -s $(pwd)/skills/gudong-tmpimg ~/.claude/skills/gudong-tmpimg
ln -s $(pwd)/skills/gudong-beautify-shot ~/.claude/skills/gudong-beautify-shot
```

链接后，在 Claude Code 中直接通过自然语言触发对应技能。

## 维护方式

- 所有技能源码在 `skills/` 目录下维护
- `~/.claude/skills/` 下只放软链接，指向本仓库
- 修改只在本仓库进行，Claude Code 通过软链接自动使用最新版本

## 命名规范

所有技能统一 `gudong-` 前缀，格式为 `gudong-{动词/名词}`：

```
skills/
├── gudong-tmpimg/          # 临时图床上传
│   ├── SKILL.md
│   └── scripts/upload.sh
└── gudong-beautify-shot/   # 截图美化
    ├── SKILL.md
    └── beautify.py
```

## License

MIT
