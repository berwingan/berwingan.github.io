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
# The Answer
- sliding window with re-computation (not best)
- streamingLLM
	- As we go up the layers, more and more attention are being allocated to the first/ earlier token.
	- so just keep the attention sink when sliding the window

<div style="font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, 'Roboto Mono', monospace; line-height:1.6;">

  <div style="margin-bottom:0.35rem;"><strong>Figure 4: The KV cache of StreamingLLM</strong></div>

  <!-- row: Generating Token 7 -->
  <div style="margin-bottom:0.4rem;">
    <div style="font-weight:600; margin-bottom:0.15rem;">Generating Token 7:</div>
    <div>
      <!-- Attention sinks (yellow) -->
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">0</span>
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">1</span>
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:8px; display:inline-block;">2</span>
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:12px; display:inline-block;">3</span>

      <!-- Rolling KV (blue) -->
      <span style="background:#9FD2FF; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">4</span>
      <span style="background:#9FD2FF; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">5</span>
      <span style="background:#9FD2FF; padding:6px 8px; border-radius:4px; margin-right:12px; display:inline-block;">6</span>

      <!-- Newly generated (red) -->
      <span style="background:#FF9AA2; padding:6px 8px; border-radius:4px; display:inline-block;">7</span>
    </div>
  </div>

  <!-- row: Generating Token 8 -->
  <div style="margin-bottom:0.4rem;">
    <div style="font-weight:600; margin-bottom:0.15rem;">Generating Token 8:</div>
    <div>
      <!-- Attention sinks (yellow) -->
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">0</span>
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">1</span>
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:8px; display:inline-block;">2</span>
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:12px; display:inline-block;">3</span>

      <!-- Evicted (dashed grey box) to indicate tokens leaving cache -->
      <span style="padding:6px 8px; border-radius:4px; border:2px dashed #9aa0a6; color:#6b6f73; margin-right:8px; display:inline-block;">4 (evicted)</span>

      <!-- Rolling KV (blue) -->
      <span style="background:#9FD2FF; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">5</span>
      <span style="background:#9FD2FF; padding:6px 8px; border-radius:4px; margin-right:12px; display:inline-block;">6</span>

      <!-- Previously generated / red region -->
      <span style="background:#FF9AA2; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">7</span>
      <span style="background:#FF9AA2; padding:6px 8px; border-radius:4px; display:inline-block;">8</span>
    </div>
  </div>

  <!-- row: Generating Token 9 -->
  <div style="margin-bottom:0.6rem;">
    <div style="font-weight:600; margin-bottom:0.15rem;">Generating Token 9:</div>
    <div>
      <!-- Attention sinks (yellow) -->
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">0</span>
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">1</span>
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:8px; display:inline-block;">2</span>
      <span style="background:#FFD86B; padding:6px 8px; border-radius:4px; margin-right:12px; display:inline-block;">3</span>

      <!-- Evicted tokens shown as dashed -->
      <span style="padding:6px 8px; border-radius:4px; border:2px dashed #9aa0a6; color:#6b6f73; margin-right:8px; display:inline-block;">4 (evicted)</span>
      <span style="padding:6px 8px; border-radius:4px; border:2px dashed #9aa0a6; color:#6b6f73; margin-right:12px; display:inline-block;">5 (evicted)</span>

      <!-- Rolling KV (blue) -->
      <span style="background:#9FD2FF; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">6</span>
      <span style="background:#9FD2FF; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">7</span>
      <span style="background:#9FD2FF; padding:6px 8px; border-radius:4px; margin-right:4px; display:inline-block;">8</span>

      <!-- Newly generated -->
      <span style="background:#FF9AA2; padding:6px 8px; border-radius:4px; display:inline-block;">9</span>
    </div>
  </div>

  <!-- legend -->
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
