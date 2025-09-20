---
title: 
draft: true
---
https://d2lang.com/blog/ascii/ 



a locally trained model that takes in pictures and spits out HTML that i can use in obsidian.



1) use JSONL Dataset Format

```jsonl
{"image_path": "images/diagram1.png", "html": "<div style='...'>...</div>"}
{"image_path": "images/diagram2.png", "html": "<div style='...'>...</div>"}
```

- `image_path` → relative path to the image in your dataset folder.
- `html` → the full HTML string inlined exactly as you’d want the model to produce.

```markdown
dataset/
  images/
    diagram1.png
    diagram2.png
  dataset.jsonl
```



1) MiniGPT-4 with TinyCLIP + small LLaMA-1B (LoRA fine-tuned)
2) BLIP-2 (Flan-T5 small)
3) Qwen-VL-Chat 1.8B
4) **BLIP-2**, **MiniGPT-4**, **LLaVA**, or **Qwen-VL**


```python
import os, json
from datetime import datetime
from some_api import send_to_chatgpt # Replace with real API call

SAVE_DIR = "dataset"
os.makedirs(SAVE_DIR, exist_ok=True)

PROMPT = """
Convert the following image into HTML with these constraints:
1. Use only inline styles.
2. No comments.
3. No blank lines.
4. Compact enough for direct paste into markdown.
5. Preserve the visual layout exactly.
"""

def process_image(image_path):
    html = send_to_chatgpt(image_path, PROMPT)
    record = {
        "image": image_path,
        "html": html.strip()
    }
    ts = datetime.now().strftime("%Y%m%d_%H%M%S")
    out_file = os.path.join(SAVE_DIR, f"sample_{ts}.json")
    with open(out_file, "w") as f:
        json.dump(record, f, ensure_ascii=False)
    print(f"Saved {out_file}")

# Example use
process_image("figures/figure4.png")
```

how to enforce the output ?
dottxt.ai


# Prompt ?
```markdown
I will give you an image of a figure.  
Please recreate it as a single HTML block that:  
1. Uses only inline styles (no external CSS).  
2. Contains no HTML comments (`<!-- -->`).  
3. Contains no blank lines — each HTML element should be on one line or separated only by necessary spaces.  
4. Uses semantic `<div>` and `<span>` tags with appropriate colors, padding, and borders to match the figure’s style.  
5. Is compact enough to be pasted directly into an Obsidian note or GitHub Pages markdown file and render identically in both.
```
