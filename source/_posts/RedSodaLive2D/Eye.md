---
title: Live2D Eye
tags:
  - Live2D
categories: animation
---

## Steps
1. 素材準備
2. 佈點
3. [Glue](Glue)
4. Set masking
5. Adjust positions
6. Set animation frames


### 素材準備

眼球Mask
眼白Mask

7. Create a square as the mask base (fill with some color)
8. Ctrl + click the layer of target (眼球/眼白)
9. Switch to the layer of mask
10. delete to remove the area of target (眼球/眼白)

### 佈點

Meshing for 眼球、眼白

眼球 - copy square vertices / stroke meshing
眼白 - you know the drill

Copy the vertices for 眼球 and paste to 眼球Mask
Copy the vertices for 眼白 and paste to 眼白Mask

### Glue
11. Multi-select 眼球and 眼球Mask
12. バインド
13. Adjust weighting (100% for 眼球)
14. Turn the mask into 0% alpha
15. Repeat same step for **眼白**


### Set Masking

瞳孔 - 眼白
Things inside eye ball - 眼白+眼球
Highlights - 眼白

### Adjust positions

Adjust the rendering order
E.g. Highlight should be below eyebrows

## Animation frames

1. Open / Close eye
	- 閉眼被開眼時眼距較短
	  {% asset_img EyeReference.png %}
2. Smile
	1. 做完開閉眼後全選並在笑顏上開key frame
	2. 從上眼瞼開始