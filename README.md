# S<sub>kill</sub>B<sub>ureau</sub>

SkillBureau，简称 SB，是一个用于集中保存个人 Codex 技能的 GitHub 技能库。

## 技能

| 技能 | 用途 | 许可证 |
|---|---|---|
| `shopping-selection` | 系统化完成商品选购，比价，质量评估和证据归档 | Apache License 2.0 |
| `sol-use-luna` | 组织 sol 主任务与 Luna 独立任务，审核差异和中间产物 | Apache License 2.0 |
| `karpathy-guidelines` | 减少 LLM 编码中的过度设计，范围漂移和验证不足 | MIT |

## 目录

```text
SkillBureau
├── skills
│   ├── shopping-selection
│   ├── sol-use-luna
│   └── karpathy-guidelines
├── LICENSE
├── NOTICE
├── THIRD_PARTY_NOTICES.md
└── README.md
```

## 使用

从本地仓库根目录执行下面的命令，可以把三个技能复制到 Codex 的个人技能目录。

```powershell
$skillNames = @("shopping-selection", "sol-use-luna", "karpathy-guidelines")
foreach ($skillName in $skillNames) {
    Copy-Item -Recurse -LiteralPath ".\skills\$skillName" -Destination "$env:CODEX_HOME\skills\$skillName"
}
```

使用前请阅读对应目录中的 `SKILL.md`。

## 许可证

除第三方内容外，本仓库使用 Apache License 2.0，完整条款见 `LICENSE`。

`skills/karpathy-guidelines` 是 MIT 许可的第三方内容，完整归属信息与许可边界见 `THIRD_PARTY_NOTICES.md` 和 `LICENSES/karpathy-guidelines-MIT.txt`。
