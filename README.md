# 中文学术论文去 AI 味 Prompt

> 面向中文工科论文场景的去 AI 味提示词，目标不是“改写成另一篇文章”，而是在尽量少改动原文的前提下，去掉常见 LLM 痕迹，保留核心期刊写作需要的严谨、克制和信息密度。

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Prompt](https://img.shields.io/badge/Type-Prompt-blue.svg)](./prompts/chinese-academic-deai-prompt.txt)
[![Language](https://img.shields.io/badge/Language-Chinese-red.svg)](./prompts/chinese-academic-deai-prompt.txt)

## 这是什么

这是一个专门为中文学术写作设计的 Prompt，主要用于处理以下问题：

- 论文段落信息点是对的，但句子一眼就能看出有 AI 腔。
- 语言看起来“正式”，实际上充满空泛词、翻译腔和机械排比。
- 修改器喜欢大改特改，结果把原文作者自己的表达节奏也改没了。
- 常规润色 prompt 会把工科论文改得像科普文，或者越改越啰嗦。

这个 Prompt 的核心原则只有一句话：

“以最小改动去除 AI 痕迹，同时保持甚至提高学术表达质量。”

## 为什么这个 Prompt 更适合中文工科论文

很多通用“降 AI 率”提示词的问题，不是改不掉，而是改偏了。这个仓库里的版本专门把边界卡得比较死：

- 不追求花哨表达，只保留核心期刊常见的严谨表述。
- 不盲目删除词语，而是要求把空词替换成具体事实或逻辑关系。
- 不把“去 AI 味”理解成“更口语化”，而是要求更精炼、更客观。
- 不默认整段重写，而是强调“少改、准改、能不动就不动”。
- 输出附带修改日志，便于核对每一次改动是否真的必要。

## Prompt 亮点

- 多角色交叉审稿：同时模拟资深工科教授、论文语言编辑和 AI 痕迹审查员。
- 强约束改写：明确限制空话、套话、伪学术术语、翻译腔和机械枚举。
- 最小干预策略：原文已经自然时，允许直接判定“检测通过”。
- Word 友好输出：正文可直接粘贴进 Word，不带 Markdown 标记。
- 可复核：输出分为“正文”和“修改日志”，适合人工快速审阅。

## 适用场景

- 中文核心期刊、EI、硕博论文正文润色
- 工科论文返修阶段的语言统一
- AI 初稿转人工终稿
- 老师审稿前的最后一轮风格净化
- 批量处理模型生成的学术段落

## 不太适合的场景

- 英文学术论文润色
- 社科、文学、新闻评论类写作
- 需要主动扩写内容、补实验、补引用的任务
- 需要“故意写得不像论文”的口语化改写

## 快速开始

### 方式一：直接复制完整 Prompt

完整版本见：

[`prompts/chinese-academic-deai-prompt.txt`](./prompts/chinese-academic-deai-prompt.txt)

带说明的 Markdown 版本见：

[`prompts/chinese-academic-deai-prompt.md`](./prompts/chinese-academic-deai-prompt.md)

把里面的完整 Prompt 发给模型，再把你的中文学术文本粘到 `[在此处粘贴你的中文学术文本]` 的位置即可。

### 方式二：把 Prompt 设成固定系统提示词

如果你经常改中文论文，可以把这个 Prompt 设成你常用模型的固定 system prompt，再在每次对话里只粘贴论文段落。

## README 直接复制版

下面这个代码块就是适合放在 GitHub README 里的“可直接复制版”。在 GitHub 页面上，代码块右上角会自动出现复制按钮，效果就和你给我的那个仓库类似。

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

## 推荐搭配模型

- Claude：对长文本、细颗粒度风格控制通常更稳。
- GPT 系列：适合快速迭代和批量处理。
- Gemini / Qwen / DeepSeek：也能用，但建议先拿几段你自己的真实论文试跑，再微调提示词细节。

关键不在模型名，而在于模型是否愿意严格遵守“最小改动”和“不要口语化”这两个约束。

## 一个典型示例

原句：

```text
值得注意的是，本文提出的方法在一定程度上提高了系统的整体性能，并为相关研究提供了新的思路。
```

更接近本 Prompt 预期的输出：

```text
所提方法提高了系统整体性能，并为后续研究提供了可复用的实现路径。
```

这里处理掉的，不只是“值得注意的是”和“在一定程度上”这种常见 AI 套话，更重要的是把“新的思路”替换成了更具体的学术表达。

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

## 使用建议

- 不要一上来就整篇论文全贴，先拿摘要、引言或讨论部分各抽一段测试。
- 如果你的导师特别强调“保留原话”，就重点观察修改日志里是否出现了不必要重写。
- 如果是某个具体学科有固定术语，先在输入文本前补一行说明“术语必须保留原写法”。
- 如果你需要的是“补内容”而不是“去 AI 味”，那应该换另一个 Prompt，不要让一个 Prompt 同时干两件相反的事。

## 如果你想把这个仓库做得更容易涨 Star

除了 README，GitHub 页面本身也很重要。建议把这几个地方一起补上：

1. 仓库名尽量改成别人一眼能搜到的名字，比如 `zh-academic-deai-prompt`、`chinese-paper-deai-prompt` 或 `academic-writing-deai-prompt`。
2. 仓库描述直接写清用途，比如：`A prompt for de-AI rewriting of Chinese academic writing, especially engineering journal papers.`
3. 主题标签建议加上：`prompt`、`academic-writing`、`chinese`、`ai-writing`、`llm`、`paper-writing`。
4. 首页首屏一定要让访问者 5 秒内看懂“这是什么、解决什么问题、怎么复制使用”。
5. 后续可以补一组真实匿名案例，对 Star 转化会很有帮助。

## License

MIT

如果这个仓库对你有帮助，欢迎点一个 Star。对这类 Prompt 仓库来说，最重要的不是“功能很多”，而是首页足够清楚、效果边界足够明确、别人复制后真的能用。
