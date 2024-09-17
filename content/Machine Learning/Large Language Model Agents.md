---
title: Large Language Model Agents 🧠 (CS 294/197-196)
tags:
  - berkeley
  - llm
---
Online course from Berkeley [here](https://llmagents-learning.org/f24)

# Syllabus
| Lecture                                | Supplemental Reading |
| -------------------------------------- | -------------------- |
| LLM Reasoning                          |                      |
| LLM Agents: Brief History and Overview |                      |

# Lecture 1: LLM Reasoning
Last Letter Concatenation Problem.

| Input        | Output |
| ------------ | ------ |
| Elon Musk    | nk     |
| Bill Gates   | ls     |
| Barack Obama | ?      |
Adding 'reasoning process' before 'answer' ?
## ==Key Idea==: Derive the Final Answer through Intermediate steps.
	-Ling et al (Program Induction by Rationale Generation: Learning to Solve and Explain Algebraic Word Problems)
	-Cobbe et al. Training Verifiers to Solve Math Word Problems
	-Nyt et al. Show Your Work: Scratchpads for Intermediate Computation with Language Models

Training, Fine tuning and Prompting with intermediate steps.
Examples with intermediate steps.

### Reasoning strategies 
1) Least-to-Most Prompting
2) "Let's think step by step" prompt
3) Recall related problem - adaptively generate relevant examples and knowledge, rather than using a fix set of examples
4) Chain-of-Thought Reasoning without Prompting (Greedy Decoding) ??
5) Self-Consistency
6) Universal Self-Consistency
7) Consensus under debate of multiple LLM
8) Oracle feedback for self-debug (unit tests)
### Test
1) Compositional Generalization
### Limitation
1) Distracted by irrelevant context
2) Cannot self-correct reasoning yet
3) Premise Order Matters in LLM Reasoning

## Concern on generating intermediate steps instead of direct answers ?
1) Probabilistic nature of LLM for token generation

### What LLM does in decoding:
$\text{arg max }\mathbb{P}\text{(reasoning path, final answer| problem)}$
### What we want:
$\text{arg max }\mathbb{P}\text{(final answer| problem)}$
#### One-step Further
$$\text{arg max }\mathbb{P}\text{(final answer| problem)}= \sum_{\text{reasoning path}} \mathbb{P}\text{(final answer| problem)}$$
## **Summary**
- Generating intermediate steps improves LLM performance
    - Training / finetuning / prompting with intermediate steps
    - Zero-shot, analogical reasoning, special decoding
- Self-consistency greatly improves step-by-step reasoning
- Limitation: irrelevant context, self-correction, premise order
### What are next? 
1) Define a right problem to work on
2) Solve it from the first principles

# Lecture 2: LLM Agents: Brief History and Overview
Agent:
	an intelligent system that interacts with some enviroment

**Types of Task**
1) Reasoning 
2) Knowledge - can be augmented with RAG
3) Computation

**Tools**
1) Search Engine, Calculator
2) Task-specific models
3) APIs
## Question and Answer Breakdown
1) Symbolic Reasoning
2) Mathematical Reasoning
3) Commonsense QA
4) Knowledge-intensive QA
5) Multi-hop knowledge-intensive QA

### Potential Tools
1) Chain of Thought
2) Tool use
3) RAG
4) Program of Thought
5) WebGPT
6) Self-ask
7) IRCoT

### ==ReAct== = Reason and Act
- cannot explore systematically or incorporate feedback
- own context space is infinite size, changed when doing the thinking
- reasoning is an internal action for agents

## Memory
### Short-Term Memory
- append-only
- limited context
- limited attention
- do not persist over new tasks
### Long-Term Memory
- read and write
- stores experience, knowledge, skills
- persist over new experience
### Reflexion
1) Task
2) Trajectory
3) Evaluation
4) Reflection (find which unit test fail from a coding example)
How does it update the memory ? 

### Cognitive Architectures for Language Agents (CoALA)
Any agent can be described with 
1) Memory
2) Action Space
3) Decision Making

#### Q
1) What distinguishes external environment vs internal memory ?
2) What distinguished long vs short term memory ?

Symbolic AI Agent -> Deep RL Agent -> LLM Agent
Language is the latent space for LLM Agents.

## Challenge
1) Reasoning over real-world language
2) decision making over open-ended actions and long horizon

## What's Next ?
1) Training - FireAct: Toward Language Agent Fine-tuning
2) Interface - SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering
3) Robustness - ==how many pass out of k?==
4) Human - $\tau$-bench: A Benchmark for Tool-Agent-User Interaction in Real-World Domains
5) Benchmark

https://princeton-nlp.github.io/language-agent-impact/
EMNLP tutorial on language agents (Nov12-16), sorry bois, the visa prob won't work out




