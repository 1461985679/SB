# S<sub>kill</sub>B<sub>ureau</sub>

Not Son of Bitch，Not Sha Bi，But Skill Bureau。

SkillBureau，简称 SB，是一个面向个人 Codex 技能的 GitHub 技能市场仓库。项目将可复用技能按插件和技能目录组织，提供安装清单，许可证说明，以及本地验证和市场索引。当前收录 shopping-selection 和 Go³。

## 技能

| 技能 | 用途 | 许可证 |
|---|---|---|
| `shopping-selection` | 系统化完成商品选购，比价，质量评估和证据归档 | Apache License 2.0 |
| `Go³` | 组织主代理与 Luna 的多模型协作，审核差异和中间产物 | Apache License 2.0 |

## 目录

```text
SB
├── .agents/plugins/marketplace.json
├── plugins/skillbureau
│   ├── .codex-plugin/plugin.json
│   └── skills
│       ├── shopping-selection
│       └── GoGoGo
├── LICENSE
├── NOTICE
└── README.md
```

## 使用

从本地仓库根目录执行下面的命令，可以把插件内的两个技能复制到 Codex 的个人技能目录。

```powershell
$skillNames = @("shopping-selection", "GoGoGo")
foreach ($skillName in $skillNames) {
    Copy-Item -Recurse -LiteralPath ".\plugins\skillbureau\skills\$skillName" -Destination "$env:CODEX_HOME\skills\$skillName"
}
```

使用前请阅读对应目录中的 `SKILL.md`。

## 许可证

本仓库使用 Apache License 2.0，完整条款见 `LICENSE`。

## 市场安装

圣上需要先在本机完成 GitHub 访问认证，再使用 Codex CLI 注册市场。

```powershell
codex plugin marketplace add 1461985679/SB --ref main
codex plugin marketplace list
```

注册市场后，圣上可以重启 Codex 桌面应用，在 Plugins Directory 中选择 SkillBureau 并安装。安装完成后，新建对话，Codex 才会加载插件内的 shopping-selection 和 GoGoGo。

官方文档支持 GitHub shorthand，HTTPS Git URL 和 SSH Git URL。仓库的访问权限由 GitHub 和 Git 凭据控制。
