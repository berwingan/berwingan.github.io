---
title: Distillation Robustifies Unlearning
date: 2025-06-14
tags:
  - unlearning
  - distillation
---

1) Suppress bad behavior to unlearn in main model
2) Distill to another model
	1) distillation process does not contain bad behavior examples ?
	2) only expressed behaviors are transferred, not latent capabilities
3) New model have ==unlearned== as well as new model from scratch without any bad behavior examples.

## Distillation makes it harder to retrain the new model to do the bad thing ?
- training sequence ?
- how to ==quantify==

## Unlearn - Noise - Distilled - on - Outputs
1) Unlearn (GradDiff, RMU) <- look up
2) Noise, corrupt the weights of the suppressed model and initialize the student as this damaged model.
	- shrink-and-perturb (scale the weights down + add noise), which weights ? pruning ?
3) Distill
# Relearning Attack 
1) Access model
2) Use small public available dataset on unlearned domain
3) fine-tunes model on the dataset -> 'jogs' the model's memory

Other attacks ?

# Finetuning = Suppressing vs Remove



# Key Idea
- The weights still contain the capability, but the model just learned how not to show that capability.
- How does re-derivation works ? 
- pruning, targeted damage (shrink-and-perturb certain path)
- distillation step by internal activation ?