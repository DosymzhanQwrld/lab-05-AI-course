# Lab 05 — Conclusion

<!--
Read this before you write.

This file is graded by your instructor, by hand, and it is worth 6 of the 15 points.

- Type it yourself. Do not use a chatbot, an AI assistant, an AI autocomplete or a "rewrite my
  text" tool for any part of it, not even for grammar. English that is plain and a little
  clumsy but yours is better than polished text that is not.
- Use your own numbers. Every number you quote must be one your own notebook printed. Copy
  the number exactly as it appeared. A number your notebook did not print is marked as wrong.
- Answer in your own words, about 80-200 words per question. A short answer that uses your
  numbers beats a long answer that could have been written by anyone.
- Delete these comment lines if you like. Keep the three headings and the last line.
-->

## 1. Which layer changed your results the most?

Give the numbers before -> after for that layer (correct / wrong / no answer, out of 20) and say
whether it changed what the agent *can do* or only what it *admits*. If no layer changed the
number of correct answers, say so and explain what the layers did change instead.

(write here)

## 2. One failure the full harness did not fix

Pick one question that the full harness (layer 3) still gets wrong or refuses. Give its id
(q01 ... q20). Open its trace in the notebook: at which step did it go wrong, and what did
the model do instead? Name one thing you would add to the harness, and what it would cost
(extra model calls, tokens, time, or a new way to fail).

(write here)

## 3. Workflow or agent for the monthly ranking?

Dala Insight wants to publish, every month, "which region is highest and which is lowest on one
indicator in one year". Would you ship the fixed workflow or the agent? Use the accuracy, the
number of model calls, the tokens and the time you measured in Part 1. Then say in one sentence
what kind of question would make you choose the other one.

(write here)

Workflow vs. Agent
The workflow had better performance on the fixed shape questions. The workflow correctly answered 13/15 questions and the agent answered 9/15. It also made 15 model calls and 3,852 tokens, while the agent made 26 calls and 19,835 tokens. The workflow was more cost-effective as they did not have to select tools repeatedly but followed a predetermined workflow. It was unable to recover from wrong region names, though. The tool did not accept the names in questions 21 and 22, and workflow did not return a response. The agent was more flexible and could try the 9 open questions and got 7/9 right. Predictable tasks, I would use a workflow; more flexible steps for questions, an agent.
Harness Layers
The bare agent answered 16/24 questions correctly, and had 4 answers wrong and 4 blanked. Layer 1 returned tool errors back to the model, and did not stop, resulting in correct answers of 18/24. It did help the agent get some invalid region names (but some unanswered questions turned into wrong answers). A step budget was added to Layer 2, but this had no effect on the results. Layer 3 assessed if there was an evidence-based response to the tools. It maintained 18 out of 24 correct answers while decreasing the number of incorrect answers from 6 to 4 and avoiding 2 answers. A number was caught that was not in the tool output in q18. However, the use of a number from a tool doesn't mean the answer is right.
Memory and Notes
I included comments for valid region names, use of tools, ranks and calculations. The notes were useful for answering the alias questions (q21 & q22) as the agent knew how to use the accepted region names. But they weren't successful in increasing accuracy overall. Both versions answered 18/24 questions correctly. There was a decrease in wrong answers from 4 to 2, and no increase in answers from 2 to 4. Questions q14 and q16 were made worse, from correct to no answer. The notes also highlighted the increase in note use from 60,116 to 72,701, and a rise in the number of model calls (which remained at 74). This illustrates that memory can repair certain errors, but it is costly and comes at the cost of less than always enhancing outcomes.

I wrote this file myself, without any AI tool.
