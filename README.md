# 闪亮的 uu 的童话创作 Skills

把细腻软萌的角色图，做成带有手绘标题的童话海报。

这里分享两个可以独立使用、也可以接着使用的 Skill。整理与分享：**@闪亮的uu爱画画**。

| Skill | 做什么 | 你需要提供什么 |
| --- | --- | --- |
| 细腻质感软萌童话风生成器 · softytale | 用 Image Gen 创作细腻微绒皮肤、柔顺发丝、差异化材质的软萌角色 | 人物、主题或道具描述 |
| 图片手绘加字 · image-handlettering | 为图片添加手绘标题和可选底部小字，自动调整配色与留白 | 原图、主标题、可选小字 |

## 获取方法

打开 [最新发布版](https://github.com/uu525/fairy-art-skills/releases/latest)，在 **Assets** 中下载：

- `softytale-skill.zip`：角色生成器，含三张风格参考图。
- `image-handlettering-skill.zip`：手绘加字，含思源黑体、字体许可证、小字脚本和四季参考图。
- `fairy-art-skills-bundle.zip`：两个 Skill 合集及中文说明。

完整源码和资源随上述发布包提供；仓库首页主要用于说明与展示。请下载 **Assets 中这三个自定义 ZIP 之一**，不要把 GitHub 自动生成的 `Source code (zip)` 或 **Code → Download ZIP** 当作完整 Skill 包。请保留整个 Skill 文件夹，只复制 `SKILL.md` 会缺少参考图或字体。

## 在 Codex 中安装

先下载合集 ZIP 并解压，再把解压文件夹交给 Codex，复制下面这段话（补上本机实际路径）：

```text
请从我下载并解压的 fairy-art-skills-bundle 文件夹（路径：填写你的实际路径），
将 skills/softytale 和 skills/image-handlettering 两个完整目录安装到当前环境支持的用户级技能目录。
请检查参考图是否完整，以及加字 Skill 的 Python、Pillow 和字体是否可用。
```

也可以手动解压，把两个文件夹放进当前项目的 `.agents/skills/`，使结构如下：

```text
.agents/skills/softytale/SKILL.md
.agents/skills/image-handlettering/SKILL.md
```

用户级安装可按当前 Codex 的技能目录设置操作。新版官方文档列出 `~/.agents/skills/`；部分现有环境使用 `~/.codex/skills/`，避免在多个目录重复安装同名 Skill。安装后若未出现，重新打开 Codex。

安装说明参考 [OpenAI 官方技能文档](https://developers.openai.com/zh-Hans/docs/build-skills)。Skill 定义工作流，不附带图像模型额度；实际生图需要所用环境具有 Image Gen 或兼容图像编辑能力。

## 直接这样用

### 生成角色

```text
用 $softytale 画一张春日女孩：柔雾粉长发，睁眼，双手捧樱花，
细腻柔滑微绒皮肤，柔和渐变背景，只有一点点虚化花影。
```

默认一张、目标 9:16、完整半身；男孩女孩、睁眼闭眼、长发短发都可指定。发色随主题变化。顶部预留约 12%–15% 自然留白，兼顾有字与无字构图。输出实际尺寸以模型结果为准。

### 给图片加字

上传原图，再发送：

```text
用 $image-handlettering 给这张图加两字手绘标题“抱春”，
底部小字写“我的春日小记 @你的名字”。
标题避开人物与道具，颜色和画面协调，小字单行居中。
```

小字可不提供，也不会自动加作者署名。想复现示例署名，可自行指定：`细腻质感软萌童话风 Skill 测试 @闪亮的uu爱画画`。

主标题由图像编辑完成；小字使用随包思源黑体精确渲染，需要 Python 3.10+ 和 Pillow：

```bash
python -m pip install -r skills/image-handlettering/requirements.txt
python skills/image-handlettering/scripts/add_footer.py 标题图.png 成品.png --text "你的小字"
```

### 连起来使用

```text
先用 $softytale 生成一个雾蓝短发、闭眼持扇的夏日男孩，
再用 $image-handlettering 加上“听风”，底部写“夏日小记 @你的名字”。
```

## 四季效果示例

以下为创作测试成品；顶部留白规则后来经过改进，实际构图不必逐像素复制这些样图。

| 抱春 | 听风 |
| --- | --- |
| ![抱春](https://github.com/uu525/fairy-art-skills/releases/download/v1.0.0/spring-lettered.png) | ![听风](https://github.com/uu525/fairy-art-skills/releases/download/v1.0.0/summer-lettered.png) |
| 拾秋 | 暖雪 |
| ![拾秋](https://github.com/uu525/fairy-art-skills/releases/download/v1.0.0/autumn-lettered.png) | ![暖雪](https://github.com/uu525/fairy-art-skills/releases/download/v1.0.0/winter-lettered.png) |

## 其他平台

支持自定义技能的平台可以参照 `SKILL.md` 配置；不保证所有平台都接受相同 ZIP 格式。仅支持提示词的平台可阅读角色 Skill 的 `references/prompts.md`，以及加字 Skill 的 `references/platform-prompt.md`。不能运行脚本的平台可采用纯 AI 小字方案，但需要人工核对错字，无法保证精确字体。

## 素材说明

思源黑体按随附 `assets/fonts/OFL.txt` 使用。角色核心参考图来自作者收集的视觉参考，其原作者和独立再分发许可未在本项目核实；本项目不将第三方参考图声明为原创，也不为其额外授予商业使用许可。参考图用于风格校准，用户可换成自己有权使用的图片。AI 生成示例仅展示效果，不保证每次输出一致。
