---
title: How Attention Sinks Keep Language Models Stable
date: 2025-08-08
tags:
  - streaming
  - transformer
source: Guangxuan Xiao
---
tokens that consistently absorb a lot of attention from other tokens, without sending much attention out.

## Paper
1) Efficient Streaming Language Models with Attention Sinks


## How to run inference beyond the hardware limit ?
1) shift the entire window forward
	- invalidating KV cache
	- keeps cache anyway ?
	- window attention don't work ?

# The Problem
- The models learn to allocate extra attention they don't need in the softmax to the first few tokens ? 
- Overmixing ?
- The higher the layers, the more attention is thrown towards the front.
# The Answer
- sliding window with re-computation (high compute)
- streamingLLM
	- As we go up the layers, more and more attention are being allocated to the first/ earlier token.
	- so just keep the attention sink when sliding the window

<div style="font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, 'Roboto Mono', monospace; line-height:1.6;">
  <div style="margin-bottom:0.35rem;"><strong>Figure 4: The KV cache of StreamingLLM</strong></div>
  <div style="margin-bottom:0.4rem;">
    <div style="font-weight:600; margin-bottom:0.15rem;">Generating Token 7:</div>
    <div>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">0</span>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">1</span>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:8px; display:inline-block;">2</span>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:12px; display:inline-block;">3</span>
      <span style="background:#9FD2FF; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">4</span>
      <span style="background:#9FD2FF; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">5</span>
      <span style="background:#9FD2FF; color:black; padding:6px 8px; border-radius:4px; margin-right:12px; display:inline-block;">6</span>
      <span style="background:#FF9AA2; color:black; padding:6px 8px; border-radius:4px; display:inline-block;">7</span>
    </div>
  </div>

  <div style="margin-bottom:0.4rem;">
    <div style="font-weight:600; margin-bottom:0.15rem;">Generating Token 8:</div>
    <div>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">0</span>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">1</span>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:8px; display:inline-block;">2</span>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:12px; display:inline-block;">3</span>
      <span style="padding:6px 8px; border-radius:4px; border:2px dashed #9aa0a6; color:#6b6f73; margin-right:8px; display:inline-block;">4 (evicted)</span>
      <span style="background:#9FD2FF; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">5</span>
      <span style="background:#9FD2FF; color:black; padding:6px 8px; border-radius:4px; margin-right:12px; display:inline-block;">6</span>
      <span style="background:#FF9AA2; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">7</span>
      <span style="background:#FF9AA2; color:black; padding:6px 8px; border-radius:4px; display:inline-block;">8</span>
    </div>
  </div>

  <div style="margin-bottom:0.6rem;">
    <div style="font-weight:600; margin-bottom:0.15rem;">Generating Token 9:</div>
    <div>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">0</span>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">1</span>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:8px; display:inline-block;">2</span>
      <span style="background:#FFD86B; color:black; padding:6px 8px; border-radius:4px; margin-right:12px; display:inline-block;">3</span>
      <span style="padding:6px 8px; border-radius:4px; border:2px dashed #9aa0a6; color:#6b6f73; margin-right:8px; display:inline-block;">4 (evicted)</span>
      <span style="padding:6px 8px; border-radius:4px; border:2px dashed #9aa0a6; color:#6b6f73; margin-right:12px; display:inline-block;">5 (evicted)</span>
      <span style="background:#9FD2FF; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">6</span>
      <span style="background:#9FD2FF; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">7</span>
      <span style="background:#9FD2FF; color:black; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">8</span>
      <span style="background:#FF9AA2; color:black; padding:6px 8px; border-radius:4px; display:inline-block;">9</span>
    </div>
  </div>
  <div style="font-size:0.92rem; border-top:1px solid #e6e6e6; padding-top:0.5rem;">
    <div style="display:flex; gap:10px; align-items:center; flex-wrap:wrap;">
      <div style="display:flex; align-items:center; gap:6px; margin-right:8px;">
        <span style="width:14px; height:14px; background:#FFD86B; display:inline-block; border-radius:3px;"></span>
        <span>Attention Sink (kept)</span>
      </div>
      <div style="display:flex; align-items:center; gap:6px; margin-right:8px;">
        <span style="width:14px; height:14px; background:#9FD2FF; display:inline-block; border-radius:3px;"></span>
        <span>Rolling KV cache (sliding window)</span>
      </div>
      <div style="display:flex; align-items:center; gap:6px; margin-right:8px;">
        <span style="width:14px; height:14px; background:#FF9AA2; display:inline-block; border-radius:3px;"></span>
        <span>Generated / recent tokens</span>
      </div>
      <div style="display:flex; align-items:center; gap:6px;">
        <span style="width:18px; height:14px; border:2px dashed #9aa0a6; display:inline-block; border-radius:3px;"></span>
        <span>Evicted tokens (dashed)</span>
      </div>
    </div>
  </div>
</div>


# What so special about the attention sinks ?
Just the fact that they are in the beginning. The position of being in front naturally makes them the stabilizers for other tokens to throw attention to.

- Create a special dedicated learnable sink at the start which can always be used for every training sample.

The positions being used is the relative position, assume that no tokens was evicted and ask the model to predict the 7th token when token 4 and 5 are missing (6->4, 7->5, 8->6) and just concatenate from 3->6 (absolute position) or rather 3->4 (relative position).


Can this be done when attention are looking both ways ? Bidirectional ?
- Big Bird BERT ?
# Intuition
1) Transformers need somewhere "safe" to put attention
	- evicted tokens can have majority of weight causing unstable shift when the window is moved -> spiking perplexity
2) Attention anchors ?
	- optimizer / weight stabilizer
3) Prevent overmixing by allowing later tokens to not mix too many concepts together and not average out the meaning of useful tokens to 0.



