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

1. Open / Close eye（開閉Keyframe）
	- 閉眼被開眼時眼距較短
	  {% asset_img EyeReference.png %}
2. Smile（笑顏Keyframe）
	- 做完開閉眼後全選並在笑顏上開key frame
	- 從上眼瞼開始
3. 眼球彈跳曲面
	- 物理演算用
4. 眼球移動（眼球XY移動曲面）作為眼球彈跳曲面的父層
	- 盡量把兩極的距離設定相等
	- 四角生成後把複製四角的sin45°數值（**0.7071**）
5. 眼球球體變形（眼球球體曲面）（Week2Day2-1, 01:13:57）
	1. Copy眼球XY移動曲面
	2. 在被copy的曲面上生成新的曲面
	3. 原地放大（Alt+Shift+Drag放大）- 分割數15×15
	4. Brush選取工具點中間（圓最好放含所有點）
	5. 原地放大（Alt+Shift+Drag放大）
	6. 重複步驟4-6幾次
	7. 全體縮小
	8. 這樣把子層曲面變成近球體形狀
	9. 把本來的球眼XY移動曲面內的物件移到新的XY移動曲面內
	    {% asset_img AfterStep5.png %}
6. 虹膜XY位差曲面（Week2Day2-1, 01:20:00）