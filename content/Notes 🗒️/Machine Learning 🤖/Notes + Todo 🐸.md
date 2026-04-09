---
title: Notes
draft: true
---
# Question
1) can contrained decoding be used to do surgery on LLM ?
2) linear prob for seeing which neuron is used for certain facts
3) memory layers ? https://jessylin.com/2025/10/20/continual-learning/
	1) # Task-Specific Skill Localization in Fine-tuned Language Models
4) Diff Interpretation Tuning (DIT) -  Tony Wang
# Todo
1) Matformer
2) Dense Attention
3) Sparse Attention
4) Radial Attention



# An Observation on Generalization
Ilya Sutskever

Unsupervised Learning via Distribution Matching
Get X and Y
Find F so that distribution(F(X))~ distribution(Y)
- substitution ciphers
- unsupervised machine translation

Prediction is ==compression==.
Compression algo C
C(concat (X,Y) < C(X) + C(Y) + O(1) 
Gap = mutual information

Kolmogorov Complexity = Compressor
- K(X) = length of shortest program that outputs X.
Joint compression = maximum likelihood

# Papers
- [ ] Colorful Image Colorization
- [ ] Mixture of Million Experts
	- [ ] combine this with mamba ? use router to choose which hidden state/ combo of hidden state.
- [ ] Dino
- [ ] RWKV
- [ ] MAMBA
- [ ] XLSTM
- [ ] RNN ? LSTM
- [ ] Flash Attention
- [ ] Cross Attention
- [ ] Self-Search Reinforcement Learning
- [ ] Predicting The Order of Upcoming Tokens Improves Language Modeling
- [ ] Nano Banana - character consistency ?
- [ ] DinoV3

# Difussion + RLHF
- [ ] Aligning Diffusion Models with RLHF
	- Stable Diffusion + RLHF was used to create images that are _more beautiful or aligned with human tastes_.
- [ ] Controlling Generations
	- Teach diffussion models to avoid undesired outputs
- [ ] Interactive/ Task-Based Alignment
	- use RLHF to optimize for prompts.
## Mech Interp
- [ ] Thought Anchors: Which LLM Reasoning Steps Matter?
- [ ] Linear Probe
- [ ] ROME (Rank-One Model Editing)
	- [ ] try for the lesswrong what LLM can see.
- [ ] next paper from ROME author
- [ ] MEMIT (Mass Editing Memory in Transformers) 
- [ ] LoRA
- [ ] Reasoning models don’t always say what they think: Chain-of-thought may omit crucial influences.
- [ ] Cats Confuse Reasoning LLM: Query-Agnostic Adversarial Triggers for Reasoning Models

### Mech Interp Questions
1) Reasoning models don’t always say what they think: Chain-of-thought may omit crucial influences.
	- ==implication== is that COT $\neq$ transparent window into reasoning
	- can't this be fine tuned away ?
	- train the model to discuss the prompt and to have COT on the prompt itself ?
		- maybe even with fine tuning the model can miss out on hints ? as the wording won't trigger appropriate steering ?

2) Reasoning for 'I don't know'. Does the attention look at similar things ? Can you expand or restrict how closely the model relaxes on things it think it knows ?
	- ==holy grail== : some parameter you can tune up or down. Up then even a typo means it does not know the thing. King Kong vs Kang Kong.
3) How many words are there in your answer ? Masked Diffusion Model vs Auto Regressive
4) Reverse Curse: Learn A is B, infer B is A. The capital of France is Paris. Paris is the capital of France.
	- ==Data Coverage== Problem: How to **encode symmetry in large LLMs** without duplicating every pair in training.
	- Related Papers
		- Mitigating Reversal Curse in Large Language Models via Semantic-aware Permutation Training
		- A simple neural network module for relational reasoning -> not really useful, detect n objects in a picture, output n embeddings, run relational MLP on each pair.
		- Hierarchical Reasoning Model ? a slow and a fast? the slow can catch Paris/France + Capital
	- Encode Base model vs Decoder based model (BERT vs GPT)
	- is there a feature that transform both A and B into C  and C + either A or B = the other thing ?
	- is there a XOR function ? in the key-value idea in the MLPs. [[ROME]]
	- ==todo== some kind of trace on the ones that work ?
	
5) 


# Attention Related
1) [[FlexAttention]]
2) Strip Self-Attention
	- deterministic downsampling/stripping -> why not make it learned like deepseek ?
	- can use google self-play RL for transcoders for videos ?
3) Adaptive Attention
4) Sparse Attention
5) Linear Attention Mechanism

# How To Read Papers
1. Category: What type of paper is this? A measurement paper? An analysis of an existing system? A description of a research prototype? 
2. Context: Which other papers is it related to? Which theoretical bases were used to analyze the problem? 
3. Correctness: Do the assumptions appear to be valid? 
4. Contributions: What are the paper’s main contributions? 
5. Clarity: Is the paper well written?