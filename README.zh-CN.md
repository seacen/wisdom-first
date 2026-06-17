# wisdom-first

> 把人类最好的思考带给你的 AI——先给框架和书，再动手。

**[English README →](README.md)**

`wisdom-first` 是一个面向 Claude Code 及其他 AI 智能体的 [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills)。在你的助手对一个值得认真思考的问题脱口给出即兴答案之前，它先去调取人类在这"类"问题上已经沉淀的最好思考：点出 2–3 个互补的框架、推荐最好的书、提炼精华，然后**透过这些视角**来解决你的问题。

*一个提升 AI「怎么思考」、而不只是「知道什么」的 skill。*

## 安装

用开放的 [`skills`](https://github.com/vercel-labs/skills) CLI——无需安装，直接 `npx`：

```bash
npx skills add seacen/wisdom-first

# 指定某个 agent
npx skills add seacen/wisdom-first -a claude-code

# 先看看里面有什么
npx skills add seacen/wisdom-first --list
```

装好后新开一个会话即可——它会自动识别 `SKILL.md`。`skills` CLI 会自动检测 Claude Code、Cursor、Codex、OpenCode 等多种 agent。

<details><summary>手动安装（clone + 软链接）</summary>

```bash
git clone https://github.com/seacen/wisdom-first.git
ln -s "$PWD/wisdom-first" ~/.claude/skills/wisdom-first
```

</details>

## 它做什么

当你来咨询，或要做一件值得认真思考的事——战略、演讲、重要的书面沟通、谈判、冲突、艰难的决定、设计——`wisdom-first` 会：

1. **调出 2–3 个互补的框架 + 最好的书**，针对*你这个具体的需求*；
2. **提炼**它们的精华，并推荐你进一步阅读；
3. **把这些视角编织在一起来解决你的问题**——让答案明显是从这些智慧里长出来的，而不是临场拍脑袋。

它会在咨询类 / 长程任务上自动触发，你也可以用 `/wisdom-first` 显式调用。

## 它有意思在哪

这个 skill 里**没有任何「领域 → 书」的查找表**。把书名写死会让它脆弱、且无法泛化。它的核心（[`references/the-taste.md`](references/the-taste.md)）是一套**纯泛化的「品味」**——几条与领域无关的判断，用来衡量针对某个需求、哪一本/哪一套思考更好：

- 诊断**真实需求**（并识别出真正卡住你的是临场与状态，而不是内容）；
- 让智慧的**覆盖范围**匹配问题的范围；
- 优先那本**定义了该领域**、给你**能上手的方法**、来自**源头**、并安装**持久心智模型**的作品；
- 给出 2–3 个互补的作品并**编织**它们，而不是只甩一本书。

仅凭这几条判断，正确的经典作品就会从模型自身的知识里自然浮现——哪怕是这个 skill 从未被告知过的领域。

### 作者的书架（可选的偏好层）

有些极好的书在模型的「先验」里太安静，再完美的泛化品味也未必稳定够到它们。[`references/authors-shelf.md`](references/authors-shelf.md) 让作者亲手种入几本私人偏爱的书，**仅作为同级候选之间的打破平局**——绝不凌驾于「是否契合」，也绝不新增领域。这是一种把「我认为什么是好的」这份品味，传递给每一个安装此 skill 的人的方式。欢迎 fork 它、换成你自己的书架。

## 示例

这个 skill 从未被喂过「领域 → 书」的清单——下面这些推荐，都是从它的泛化品味里自然长出来的。它会自行调出的那一类作品举例：

| 当你在处理…… | 它倾向于调出…… |
| --- | --- |
| 一场演讲，而你很紧张 | 一本讲临场与表达的经典（作者书架里种了 *As We Speak*），再配一个「让人记得住」的框架 |
| 和伴侣 / 朋友 / 同事的冲突 | 《非暴力沟通》（Marshall Rosenberg） |
| 一封要让老板秒懂的汇报 / 邮件 | 《金字塔原理》（Barbara Minto）+ MECE |
| 企业战略，产品摊得太薄 | 《Playing to Win》（Lafley & Martin）与「战略即取舍」的级联 |
| 工作与生活里感到迷茫、原地打转 | 《高效能人士的七个习惯》（Stephen Covey） |
| 一场你怕会谈崩的谈判 | 《Getting to Yes》（Fisher & Ury）与 BATNA |

……然后它会提炼出真正要紧的那几步，编织进你**实际**的答案里。

## 它是怎么打磨出来的

`wisdom-first` 是用多智能体评估工作流开发和验证的：每个候选版本都在一批真实场景上做*带 skill vs. 裸跑*的对照（演讲、战略、人生迷茫、人际冲突、商务写作、谈判、习惯养成、一次零停机的技术迁移），每个场景跑 3 次看稳定性，并按以下标准打分——是否召回了正确的经典作品、是否让智慧的范围匹配了问题、以及是否**真的用上了**框架而非只是甩书名。那些**听起来**很对、却被数据证明有害的规律（比如「永远优先那本重新定义问题的书」）被一一抓出并回退。你现在看到的这套品味，是经受住证据检验后留下来的。

## 目录结构

```
SKILL.md                      # 触发条件 + 三步法 + 输出形态
references/
├── the-taste.md              # 核心：8 条与领域无关的纯泛化选择判断
├── authors-shelf.md          # 可选的个人偏好层（仅打破平局）
└── applying-via-workflow.md  # 把「解题」一步升级为多智能体 Workflow
evals/
└── evals.json                # 验收场景
```

## 许可证

[MIT](LICENSE) © 2026 Seacen Zhao

## 致谢

- 作为 [Anthropic Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills) 编写。
- 通过 Vercel Labs 的开放 [`skills` CLI](https://github.com/vercel-labs/skills) 安装。
