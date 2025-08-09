---
draft: true
---
# Background
## SGD with Momentum
if multiple steps of gradient descent is in the same direction, you can take larger steps. Beta is how influential past velocity will be for the next step. 
![[Pasted image 20250718202621.png]]
Exponentially weighted average of the gradients.
![[Pasted image 20250718202804.png]]
## Nesterov Accelerated Gradient
Take the same step as before then take a corrective step .

## RMSProp (Adaptive Gradient)
When gradient is predominantly in one direction and flat on another.
When there is sparse data.
Take larger step in one direction, and smaller step in another direction.
Same as 'SGD with Momentum' with some change.
Normalize varying size of gradient.
![[Pasted image 20250718232418.png]]
- $s_t​$: running average of squared gradients
- $\beta$: decay factor (e.g. 0.9)
- $\epsilon$: small constant to avoid division by zero
- Large gradients → large squared value → large denominator → smaller effective step    
- Small gradients → small denominator → larger effective step

## AdaGrad
RMSProp without weighing the past.
## Adam
RMSProp (Adaptive Learning Rate) + SGD Momentum
![[Pasted image 20250718233148.png]]
bias correction because $m_0$ and $v_0$ is initialized to 0. The early steps are biased towards 0. 
$B_1^t$ is just the beta factor used by momentum raised to a certain power at step t and shrink towards 0.
$B_2^t$ for RMS.

## AdamW (Weight Decay Fixed Adam)
Issue with original Adam was the L2 regularization ($\lambda\theta_t$) inside the gradient update.
![[Pasted image 20250718234105.png]]
Decouples weight decay from the gradient update.
==Correct==
![[Pasted image 20250718234143.png]]

## AdamC (Adam with Curvature/Confidence)
Fix instability in Adam due to high variance in the adaptive learning rate denominator $\sqrt{\hat{v}_t}$.
Add confidence term $\gamma_t^2$ to stabilize denominator.
![[Pasted image 20250718235041.png]]
Add moving estimate of the ==variance== of the adaptive learning rate itself.
![[Pasted image 20250719001246.png]]
The beta here is a brand new hyper-parameter, nothing to do with the beta used for 1st or 2nd moment.

# Non Opt Background
## ReLU
- dying ReLU when gradients goes negative
- use batch normalization ?
- encourage sparsity in activations, reduce overfitting
- works like a regularizer-ish
- used aggresively in ResNets between residual blocks.
## Dropout
- regularization technique
- during training, randomly "drop out" (set to 0) a percentage of neurons on each forward pass.
- introduce sparsity like ReLU
- protects against co-adaptation, force each neuron to work independently
- [[Rate-In: Adaptive Dropout for Better Uncertainty in Vision]]
	- Monte Carlo Dropout
		- used to estimate uncertainty, using dropout at inference time, do sampling.
	- Idea
		- Input-Adaptive Dropout During Training
		- Dropout + Gradient Flow Control
			- mechanism to control information and gradient flow (flow matching) ?
		- Learning Dropout Distributions
			- learn continuous or structured noise distribution
			- combine with attention weights to regularize attention layers selectively
		- Dropout for transformer
		- Dropout for Data Space
## Gradient Accumulation
- less noisy gradients when you use larger batches
## Batch Normalization
- normalizing activations during training to get consistent mean and variance, between layers
- [[Small Batch]]
- 
## Weight Decay (L2 Regularization)
- penalize large weights
# Learning Rate Decay Schedules
## Cosine
Follow top half of cosine curve.
```
LR
│     ***
│    *   *
│   *     *
│  *       *
│ *         *
│*           *
└──────────────→ Step

```
## Exponential
Learning rate shrinks by a fixed factor every few steps.
```
LR
│*         
│**        
│****      
│*****     
│*******   
│**********
└────────────→ Step

```

## Warmup + Cool Down
Warm Up: Start with low learning rate, ramp up to peak.
Decay: After reaching peak, slowly reduce it (cosine or exponential decay)