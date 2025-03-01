---
title: Redsoda Live2D 物理運算
tags:
  - Live2D
categories: animation
---

## 使用例子
- 乳搖
- 頭髮

## 如何進入
{% asset_img selectPhySim.png %}

## 概念
- 樹幹
- 樹枝
樹幹帶動樹枝，樹幹起頭，樹枝後面自己搖

## 實際操作
1. 追加→命名群組

{% asset_img firstStep.png %}

### 入力設定 
樹幹之地
{% asset_img inputs.png %}
1. 按右方的追加，選取作為樹幹的物件

| 入力   | 種別    | 影響度 | 反転      |
| ---- | ----- | --- | ------- |
| 樹幹物件 | 位置/角度 | %   | boolean |

### 出力設定 
樹枝之地
{% asset_img outputs.png %}
1. 按追加，選取作為樹枝的物件

| 振り子No   | 出力   | 影響度 | 反転      | 倍率     | 最大出力 |
| ------- | ---- | --- | ------- | ------ | ---- |
| 對應下方振り子 | 樹枝物件 | %   | boolean | 對應參數數字 | 純顯示  |

### 振り子
{% asset_img furiko.png %}

| 振り子No | 長さ       | 揺れやすさ | 反応速度    | 収束の早さ |
| ----- | -------- | ----- | ------- | ----- |
| ID    | 愈長擺動幅度愈大 | 愈大愈好搖 | 愈大愈快開始搖 | 愈大愈快完 |

## 建議
- 最大出力不要超過100%，會有急停的現象


## 在動畫區Bake

{% asset_img BakeAnimation.png %}

{% asset_img BakeSetting.png %}

