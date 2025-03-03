---
title: Live2D 眉
tags:
  - Live2D
categories: animation
---

## 路徑建議
{% asset_img path.png %}

Add extra vertex on the end.
So that the path does not affect too much far on default setting. (Could fine tune setting to achieve similar effect)

## PhySim

### RedSoda睫毛 Parameters

入力

| 入力   | 種別  | 影響度 |
| ---- | --- | --- |
| 左目開閉 | 位置  | 70% |
| 角度Y  | 位置  | 20% |

振り子

| 長さ  | 揺れやすさ | 反応速度 | 収束の早さ |
| --- | ----- | ---- | ----- |
| 6.6 | 0.96  | 1.06 | 1.03  |
建議每一個睫毛都分成不同的群組，然後每個振り子都有差別，令晃動比較不