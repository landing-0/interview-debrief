# interview-debrief

> 一个 Claude Code Skill，给定飞书妙记 URL，自动拉取逐字稿、深度分析面试表现、生成飞书文档并通过 IM 发送链接。

## 功能

- **自动拉取逐字稿**：从飞书妙记 URL 提取逐字稿全文
- **说话人识别**：自动判断面试官与候选人，计算发言时长占比
- **12 维度深度分析**：
  1. 基本信息（时长、面试官数量、发言比例）
  2. 逐题回答质量评分（1-5 分）
  3. 表现量化（结构/深度/表达/抗压各 /10）
  4. 错过的展示机会（Missed Opportunities）
  5. 候选人反问质量
  6. 面试官信号解读（深挖点、红旗信号）
  7. 机会评估（业务成长性、团队成熟度等）
  8. 通过率预测（按面试官类型加权）
  9. 下一轮预测与准备建议
  10. 行动清单（P0/P1/P2）
  11. 能力资产沉淀
  12. 一句话复盘总结
- **自动生成飞书文档**：按标准模板写入「我的空间」
- **IM 通知**：将文档链接发送给自己

## 依赖

- [lark-cli](https://github.com/larksuite/cli)（已安装并完成授权）
- Claude Code

## 安装

```bash
# 克隆到 Claude Code skills 目录
git clone https://github.com/landing-0/interview-debrief ~/.claude/skills/interview-debrief

# 或手动复制
cp SKILL.md ~/.claude/skills/interview-debrief.md
```

## 所需 Scope

```
vc:note:read
minutes:minutes:readonly
minutes:minutes.artifacts:read
minutes:minutes.transcript:export
```

如缺少，运行：

```bash
lark-cli auth login --scope "minutes:minutes:readonly minutes:minutes.artifacts:read minutes:minutes.transcript:export" --no-wait
```

## 使用

在 Claude Code 中直接说：

- "分析这场面试：https://xxx.feishu.cn/minutes/obcXXXX"
- "面试复盘 https://xxx.feishu.cn/minutes/obcXXXX"
- "看下这场面试"

Skill 会自动触发，完成后在飞书收到文档链接。

## 示例输出

生成的飞书文档包含：

| 章节 | 内容 |
|------|------|
| 基本信息 | 时长、面试官数、发言占比 |
| 问题全景 | 逐题质量评分表格 |
| 表现量化 | 结构/深度/表达/抗压雷达 |
| 错过的机会 | 信号词匹配度分析 |
| 通过率预测 | 按面试官类型加权得分 |
| 行动清单 | P0/P1/P2 优先级拆解 |

## License

MIT
