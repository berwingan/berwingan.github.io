---
title: Intro To Mech Interp
draft: true
---
==Hypothesis==: Models learn human-comprehensible algorithms and can be understood, if we learn how to make it legible.

Grokk? eventually generalize ?
# Sparse Autoencoders + Superposition
__Hope__: Neurons = features ?
__Problem__: Polysemanticity
__Hypothesis__: Superposition

Represent more features than dimension

Linear Representation Hypothesis

__Solution__: Sparse Autoencoders (wide)

==My Question==: when does a concept split ? under what condition ? in a SAE can you combine the same concept from 2 different neurons ?

What concepts comes together in the same neurons ?
Are they affected by how close together they are trained ?
The more important things will get more circuit ? Goal seeking ?
Forgetting a word ?
Distribution of concepts learned ?

Feature that shows the 'GOAT' ? Michel Jordan ? other western style athletic which are used with the word 'GOAT' ? Ronaldo ? how far does the relation carry ? cow ? great ? time ?
how do associations work ? can i tweak something so that the idea is now tied to a new concept ? like saying different athlete is the goat ? how to tweak it to seem natural ?
how to identify when something has been tweaked ?

Are all athletes ideas located in a similar space ?
Are athletes of a similar kind (football, basketball, judo) located in a similar space ?
Are ideas of sports located in similar space ? 
Is there some kind of algo we can find (sport + goat) in terms of location of where to look ?
Can features migrate ? in terms of where they are located (which neurons) ?

straight up deactivating neurons related to concepts.
increase activation in fish but decrease activation in ocean and other sea animals ?

# To Read
1) Progress Measures for Grokking via Mechanistic Interpretability
2) Open Problems: Interpreting Algorithmic Models
3) Golden Gate Claude
4) Sparse Feature Circuits (Sam Marks et al)
5) Neuronpedia.org
6) Gemma Scope: Open Sparse Autoencoders Everywhere All At Once on Gemma 2
7) Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet
8) Scaling and evaluting sparse autoencoders
9) Sparse Cross Coders ?

# Open Problems
- Applying SAEs to real-world tasks: hallucinations, jailbreaks, finding adversarial examples, debugging weird behaviours
- Making better SAEs (Gated, TopK, JumpReLU, etc) – better reconstruction, more interpretable, faster to train, etc – they’re expensive!
- Measuring SAE performance – it’s hard!
- Scalably finding SAE circuits – what’s really going on inside models?
- Red-teaming SAEs – are they doing what we think they’re doing? How big a deal is the error term?
- **Opportunity:** My team is releasing hundreds of SAEs on every layer and sublayer of Gemma 2 2B & 9B in a few weeks, let me know if you want early access!
