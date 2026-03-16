# 中文学术论文去 AI 味 Prompt

> 复制即用，专门给中文硕博生、科研工作者和论文返修场景准备的去 AI 味 Prompt。  
> 它不负责帮你“编内容”，只负责把已经写出来的内容改得更像一个正常科研作者写的，而不是像模型批量吐出来的。

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Prompt](https://img.shields.io/badge/Type-Prompt-blue.svg)](./prompts/chinese-academic-deai-prompt.txt)
[![Language](https://img.shields.io/badge/Language-Chinese-red.svg)](./prompts/chinese-academic-deai-prompt.txt)

## 这仓库是干什么的

如果你有下面这些场景，这个仓库就是给你准备的：

- 论文已经写出来了，但读起来一股 AI 腔，不敢直接交导师。
- 摘要、引言、讨论部分总觉得“像是对的”，但句子虚、空、套。
- 你不想自己一段段手工抠措辞，只想找一个能直接复制、马上见效的 Prompt。
- 你已经越来越依赖大模型写初稿，但又怕最后交上去的文字太像模型写的。
- 返修时间很赶，最缺的不是知识，而是最后一轮语言净化的耐心。

这个 Prompt 的目标不是把论文改得花里胡哨，而是帮你省掉最烦的那一步：

把“内容没问题但 AI 味太重”的中文学术文本，尽量少改地处理成更像中文核心期刊写作的表达。

## 为什么很多人会需要它

现在很多硕博生和科研工作者的真实工作流，已经不是“纯手写论文”，而是：

1. 自己先搭结构、写数据和方法。
2. 用模型帮忙起草一部分段落。
3. 再花大量时间手动去掉那种一眼能看出来的 AI 套话。

真正浪费时间的，通常不是“写不出来”，而是下面这些重复劳动：

- 反复删“值得注意的是”“综上所述”“具有重要意义”这种空话。
- 把机械式排比和翻译腔句子改回正常中文学术表达。
- 明明只想小修，结果模型动不动整段重写，把原意也带偏。
- 导师一句“这段 AI 味太重，重写”，你又得重新抠一遍。

这个仓库解决的就是这件事。

## 这个 Prompt 的核心特点

- 直接复制就能用，不需要你先学一堆 Prompt 工程技巧。
- 专门针对中文工科学术写作，不是泛化的“降 AI 率”模板。
- 强调最小干预，不会默认把你的原文改成另一篇文章。
- 明确限制空话、套话、伪学术词、翻译腔和机械枚举。
- 输出带修改日志，你能快速核对它到底改了什么。
- 适合返修前最后一轮清洗，也适合批量处理模型初稿。

## 适合谁

- 正在写硕士论文、博士论文的学生
- 需要投中文核心、EI 或中文学术期刊的作者
- 经常让大模型辅助写摘要、引言、讨论的科研工作者
- 想提高文字完成度，但不想把时间全耗在人工润色上的人
- 想保留自己原文技术内容，只去掉明显 AI 痕迹的人

## 不适合谁

- 想让模型替你补实验、补结果、补引用的人
- 想把论文改成更口语化、更像自媒体文章的人
- 主要处理英文论文润色的人
- 希望模型大幅重写、重组论证结构的人

## 你能直接怎么用

最简单的方式就是两步：

1. 复制下面这段完整 Prompt。
2. 把你的中文论文段落粘进去直接跑。

如果你平时已经固定用某个模型，也可以把这段 Prompt 放进 system prompt 里，后面每次只贴论文内容。

## README 直接复制版

下面这个代码块就是可以直接复制使用的版本。在 GitHub 页面里，代码块右上角会自动出现复制按钮。

```text
# Role

You will now simulate three reviewers who jointly proofread and rewrite a Chinese academic text:

- Reviewer A: A senior engineering professor at a top Chinese university with 20 years of experience reviewing for core journals such as Journal of Mechanical Engineering, Chinese Journal of Computers, and Acta Automatica Sinica. Zero tolerance for empty rhetoric, but equally opposed to turning academic papers into popular science articles.
- Reviewer B: A senior scientific paper editor specializing in language polishing for revision manuscripts. Expert at identifying translationese, mechanical enumeration, and logical gaps, while strictly maintaining academic formality and information density.
- Reviewer C: An academic integrity auditor familiar with AI-generated text patterns. Can precisely identify typical LLM phrasing habits, but will never sacrifice academic conciseness just to remove AI flavor.

The three reviewers must reach consensus and jointly produce a final draft. The rewrite must strictly follow the constraints below.

# Task

Please perform a de-AI rewrite of the provided Chinese text, making its language style rigorous, objective, and fluent, suitable for direct pasting into Microsoft Word as a formal paper submission to a Chinese core journal (engineering).

# Constraints

## 1. Stylistic Baseline

The rewritten text must maintain the formal register of Chinese engineering academic papers:
- Information density: every sentence must carry concrete technical information or advance the logical argument. No filler, no padding for fluency.
- Concise wording: prefer established concise academic expressions. For example, "具有直接影响" is better than "关系到"; "已成为...的常用方法" is better than "更多用于"; "在保证...的同时减少了..." is better than "提供了新的实现方式,可在一定程度上提高...".
- Register positioning: the target readers are fellow researchers, not general audiences. Do not turn an academic paper into explanatory prose. Maintain the brevity and precision expected of professional papers.
- Preserve the accuracy of core technical terminology. Never replace domain-specific terms just to remove AI flavor.

## 2. Vocabulary Normalization (Intent-Driven)

Replace the following types of expressions with concrete, objective academic descriptions:
- Emotional filler with no substantive information, e.g. "毋庸置疑" "不可磨灭" "至关重要" "意义深远" "深刻" "值得注意的是" "切中要害".
- Pseudo-academic jargon, e.g. "范式转移" "颠覆性" "赋能" "耦合内聚" "底层逻辑" "全链路".
- AI-frequent boilerplate, e.g. "本文旨在" "综上所述,本文提出了一种新颖的" "在当今快速发展的...背景下" "为...提供了有力支撑" "展现出巨大的潜力".
- Replacement principle: do not simply delete. Ask what fact this word is actually stating, then use that fact itself as the replacement. The replacement must not reduce the sentence's information density or academic formality.

## 3. Sentence Structure Naturalization (Remove Translationese and Mechanical Patterns)

- Eliminate long attributive chains: avoid English-style stacked modifiers like "一个基于...并结合了...的...的...方法". Split into short sentences or restructure to follow Chinese conventions of stating the main clause first, then adding modifiers.
- Limit passive voice: Chinese academic writing uses fewer "被" constructions. Prefer subjectless sentences or active voice, e.g. change "...被用来优化..." to "采用...优化...".
- Handle lists flexibly: avoid mechanical "首先...其次...最后..." or "1. 2. 3." enumeration. Usually merge into logically coherent paragraphs with natural causal or progressive transitions. However, if enumeration is genuinely clearer in context (e.g. algorithm steps or system constraints), numbered lists may be retained.
- Paragraph transitions: ensure logical transitions between paragraphs rather than abrupt jumps. Avoid starting every paragraph with "此外" "同时" "另外".
- Prevent colloquial regression: removing translationese does not mean reducing formality. Colloquial expressions like "关系到" "更多用于" "也常用于" should be elevated to more concise academic expressions like "直接影响" "主要应用于" "亦有广泛应用".

## 4. Formatting (Word-Compatible)

- No Markdown syntax: the output must not contain any Markdown markers such as bold, italic, or heading symbols. Ensure the text can be directly pasted as plain text into Word.
- Preserve necessary formulas: if the original text contains mathematical formulas or variables, embed them naturally in the Chinese text.
- Separate paragraphs with blank lines only.

## 5. Modification Threshold (Critical)

The core goal is to remove AI traces while maintaining or even improving academic expression quality, NOT to rewrite a new article:
- Less is more: if the input text is already natural, rigorous, and shows no obvious AI characteristics, preserve the original. Do not modify for the sake of modifying.
- Minimal intervention: for high-quality text with only minor flaws, fix only the confirmed issues and leave everything else unchanged.
- Every change must be justified: each modification must point to a specific problem in the original (e.g. a filler word, a translationese pattern), not subjective preference.
- Respect author style: within the above constraints, preserve the author's own word choices and writing rhythm.
- No downgrading: the modified text must not be lower in academic formality or information density than the original. If a modification makes the expression more colloquial or looser, that modification is invalid and must be reverted.
- Positive feedback: for high-quality input, provide explicit affirmation and positive evaluation in Part 2.

# Execution Protocol

Before outputting, self-check:
1. Authenticity check: does it read like a paper written by a rigorous Chinese engineering scholar for a core journal? If any part reads like popular science or colloquial narration, revise it.
2. Purity check: are all Markdown symbols removed for direct Word pasting?
3. Necessity check: does each modification genuinely improve academic coherence? If a change is just word-swapping, revert it and mark as "passed".
4. Conciseness check: compare before and after - is information density maintained or improved? If there is any padding for fluency, tighten the expression.

# Output Format

Output only the following two parts, with no extra dialogue or explanation:

Part 1 [正文]
Output the rewritten plain text (if the original is already good enough, output the original). Text should have clear paragraph breaks and no formatting symbols.

Part 2 [修改日志]
If modifications were made: briefly list which typical filler expressions, translationese patterns, or structural issues were changed.
If only minor adjustments were made: list the changes and note that the original was of high overall quality with only minor tuning.
If no modifications were made: output "[检测通过] 原文表达严谨自然,符合中文核心期刊工科论文的写作规范,无明显AI痕迹。文本逻辑清晰、用词准确、句式流畅,建议保留原文。"

# Input

[在此处粘贴你的中文学术文本]
```

## 如果你懒得自己拼接，这样用就行

你可以直接把下面这个模板发给模型：

```text
请严格执行以下 Prompt，不要省略任何约束，也不要为了改写而改写：

[把上面的完整 Prompt 粘贴到这里]

以下是原文：

[把你的中文学术文本粘贴到这里]
```

## 一个很真实的使用场景

你不是不会写，你只是没时间一遍遍手动去掉这些话：

- 值得注意的是
- 具有重要意义
- 在一定程度上
- 为后续研究提供了新的思路
- 综上所述，本文提出了一种新颖的

这些表达最大的问题不是“看着像 AI”，而是它们会稀释论文的信息密度，让整段话显得虚、满、空。

这个 Prompt 做的事很直接：

在不乱改术语、不乱改逻辑、不强行重写的前提下，把这类表述尽量压缩掉，换成更像正常学术写作的表达。

## 示例

原句：

```text
值得注意的是，本文提出的方法在一定程度上提高了系统的整体性能，并为相关研究提供了新的思路。
```

处理后更接近的结果：

```text
所提方法提高了系统整体性能，并为后续研究提供了可复用的实现路径。
```

这里不是简单删词，而是把空泛表达替换成更具体的学术表述。

## 推荐使用方式

- 摘要：最容易暴露 AI 味，优先处理。
- 引言：尤其适合清理背景段里的套话和空话。
- 讨论与结论：最容易出现“意义重大”“潜力巨大”这类机械表达。
- 返修稿：适合在提交前做最后一轮净化。

## 使用建议

- 先拿 1 到 3 段试跑，不要一上来整篇全贴。
- 如果术语很固定，先补一句“专业术语、变量和公式必须保留原写法”。
- 如果你导师特别在意作者风格，重点看修改日志有没有过度改写。
- 如果你需要的是补内容，不是去 AI 味，那就别让一个 Prompt 同时做两件事。

## 仓库结构

```text
.
├─ README.md
├─ prompts
│  ├─ chinese-academic-deai-prompt.txt
│  └─ chinese-academic-deai-prompt.md
└─ examples
   └─ sample-usage.md
```

## 备用文件

- 纯文本版 Prompt：[`prompts/chinese-academic-deai-prompt.txt`](./prompts/chinese-academic-deai-prompt.txt)
- 带说明版 Prompt：[`prompts/chinese-academic-deai-prompt.md`](./prompts/chinese-academic-deai-prompt.md)
- 简单示例：[`examples/sample-usage.md`](./examples/sample-usage.md)

## 如果你准备把它发给同学、实验室或导师

这类 Prompt 最容易传播的点，不是“理论多强”，而是：

- 别人复制一次就能用
- 用完确实能少改很多废话
- 不需要重新学习复杂规则
- 能快速看懂边界，不怕乱改论文内容

所以这个仓库首页已经尽量按“打开就会用”的方式写了。你直接发仓库链接，别人就能在首页复制。

## License

MIT

如果这份 Prompt 确实帮你省下了返修和润色时间，欢迎点个 Star。  
对这类仓库来说，Star 的意义不只是收藏，也是让更多还在手工抠 AI 腔的硕博生更快找到它。
