<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo/logo-wordmark-dark.svg">
  <img src="assets/logo/logo-wordmark.svg" alt="wisdom-first" width="420">
</picture>

<br>

**<em>先</em>拓宽你自己的认知边界，AI 才动手解题。**

**🌐 Language:** [**English**](README.md) · **中文（本页）**

[![version](https://img.shields.io/badge/version-3.0.0-EFE8D8?style=flat-square&labelColor=1B2C40)](https://github.com/seacen/wisdom-first/releases/tag/v3.0.0)
[![license](https://img.shields.io/badge/license-MIT-EFE8D8?style=flat-square&labelColor=1B2C40)](LICENSE)
[![format](https://img.shields.io/badge/format-Agent%20Skill-EFE8D8?style=flat-square&labelColor=1B2C40)](https://docs.claude.com/en/docs/agents-and-tools/agent-skills)
[![install](https://img.shields.io/badge/install-skills%20CLI-EFE8D8?style=flat-square&labelColor=1B2C40)](https://github.com/vercel-labs/skills)

</div>

---

`wisdom-first` 是一个 [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills)——一份任何 AI 智能体都能加载的通用能力。当你抛给助手一个值得认真想想的问题时，它不会张口就来、即兴作答，而是先去调取人类在这"类"问题上早已沉淀下来的最好思考：点出两三个互补的框架、推荐最值得读的书、把精华提炼出来，然后**透过这些视角**来解决你的问题。

## 它真正的价值：拓宽的是**你**的见识，不只是 AI 的

用 AI 最省事的方式，是把判断权交出去、答案照单全收。你拿到了结果——却停在「知其然而不知其所以然」的地方，而且每用一次就更依赖它一分。

`wisdom-first` 想做的恰恰相反。它会把真正用到的框架点名说清、把最要紧的那几步提炼出来、再把你引回原著——让每一个答案同时也是一堂课，而不只是一个「今天怎么办」的结论。检索和综合交给 AI，**见识留给你自己。**

这就是它押的注——让 AI 把你变得更有智慧，而不是让你越来越离不开它。

## 安装

用开放的 [`skills`](https://github.com/vercel-labs/skills) CLI——不用装任何东西，一行 `npx` 就够了：

```bash
npx skills add seacen/wisdom-first
```

装完新开一个会话即可——它会自动读取 `SKILL.md`。`skills` CLI 会自动识别你正在用的智能体，并装到对的位置。

## 它做什么

当你来求个建议，或者要做一件值得好好思考的事——定战略、准备演讲、写一封分量很重的信、扛一场谈判、化解一次冲突、拿一个艰难的主意、做一份设计——`wisdom-first` 会：

1. 针对*你眼下这个具体的需求*，**调出两三个互补的框架 + 最值得读的书**；
2. **提炼**它们的精髓，并建议你进一步读原著；
3. **把这几个视角编织到一起来解决你的问题**——让答案明显是从这些智慧里来的，而不是临场拍脑袋。

在咨询类、长周期的任务上它会自己触发，你也可以用 `/wisdom-first` 直接点名调用。

## 它怎么挑——不靠一张对照表

这个 skill 里**没有任何「领域 → 书」的对照表**。把书名写死，只会让它又脆又死板、根本无法泛化。它的核心（[`references/the-taste.md`](skills/wisdom-first/references/the-taste.md)）是一套**纯粹而通用的「品味」**——几条与具体领域无关的判断，用来衡量：针对某个需求，哪一套思考比另一套更好。

- 先诊断**真实的需求**（并且认出：真正卡住人的，往往是临场状态和心气，而不是内容本身）；
- 让智慧的**覆盖面**去匹配问题的大小；
- 优先那本**定义了该领域**、给出**能上手照做的方法**、来自**第一手源头**、并给你装上一套**用得长久的模型**的作品；
- 拿出两三本互补的书并把它们**编织**起来，而不是甩一个书名了事。

单凭这几条判断，对的经典之作就会从模型自己的知识里自然浮现——哪怕是这个 skill 从没被告知过的领域。

### 作者的书架（可选的偏好层）

有些极好的书，在模型的「先验」里太安静了，再完美的通用品味也未必每次都稳稳够到它们。[`references/authors-shelf.md`](skills/wisdom-first/references/authors-shelf.md) 让作者亲手埋进几本私藏偏爱，**仅在同级候选之间用来打破平局**——绝不会压过「是否契合」，也绝不会硬塞进一个不搭的领域。这是一种把「我认为什么才算好」的眼光，传给每一个安装者的方式。欢迎 fork 它，换成你自己的书架。

## 示例

这个 skill 从没被喂过「领域 → 书」的清单——下面这些推荐，全是从它的通用品味里自然长出来的。它会自己调出的那一类作品，举几个例子：

| 当你在忙…… | 它往往会调出…… |
| --- | --- |
| 一场演讲，而你正为它紧张 | 一本讲临场与表达的经典（作者书架里埋了 *As We Speak*），再配一个「让人记得住」的框架 |
| 和伴侣 / 朋友 / 同事闹的一次冲突 | 《非暴力沟通》（Marshall Rosenberg） |
| 一份要让老板一眼看懂的汇报 / 邮件 | 《金字塔原理》（Barbara Minto）+ MECE |
| 公司战略，产品线摊得太薄 | 《Playing to Win》（Lafley & Martin）与「战略即取舍」的级联 |
| 工作和生活里都感到迷茫、原地打转 | 《高效能人士的七个习惯》（Stephen Covey） |
| 一场你怕会谈崩的谈判 | 《Getting to Yes》（Fisher & Ury）与 BATNA |

……接着，它会把真正要紧的那几步提炼出来，编织进你**实际**要的那个答案里。

## 它是怎么打磨出来的

`wisdom-first` 是用多智能体评估工作流一版一版磨出来、验出来的：每个候选版本都拿一批真实场景做「带 skill vs. 裸跑」的对照（演讲、战略、人生低谷、人际冲突、商务写作、谈判、习惯养成、一次零停机的技术迁移），每个场景各跑 3 次看稳不稳，再按这几条打分——有没有召回对的经典、有没有让智慧的覆盖面匹配问题的大小、以及有没有**真的用上**框架而不只是甩书名。那些**听着**很有道理、一放到数据里却帮倒忙的规则（比如「永远优先那本重新定义问题的书」），都被一条条揪出来退了回去。你现在看到的这套品味，是扛过证据检验后活下来的那一版。

## 目录结构

```
skills/wisdom-first/
├── SKILL.md                  # 触发条件 + 三步法 + 输出形态
└── references/
    ├── the-taste.md          # 核心：8 条与领域无关的纯通用选择判断
    ├── authors-shelf.md      # 可选的个人偏好层（仅用于打破平局）
    └── applying-via-workflow.md  # 把「解题」这一步升级为多智能体 Workflow
.claude-plugin/plugin.json     # Claude Code 插件清单
brand.md                       # 品牌定义——图形、用色、字体、语调
assets/logo/                   # logo 资产（SVG + PNG）与用法规范
evals/
└── evals.json                # 验收场景
```

## 许可证

[MIT](LICENSE) © 2026 Seacen Zhao

## 致谢

- 基于 [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills)——扩展 AI 智能体的开放格式——构建。
- 通过 Vercel Labs 的开放 [`skills` CLI](https://github.com/vercel-labs/skills) 安装。
