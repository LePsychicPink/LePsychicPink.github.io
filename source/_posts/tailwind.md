---
title: Tailwind
date: 2024-11-24 21:48:28
tags: Tailwind
categories: programming
---

## Layout

### Aspect ratio

| value         | equals             |
| ------------- | ------------------ |
| aspect-auto   | aspect-ratio: auto |
| aspect-square | aspect-ratio: 1/1  |
| aspect-video  | aspect-ratio: 16/9 |

### container

example: `<div class="container sm">`

| value  | equals            |
| ------ | ----------------- |
| `None` | width: 100%       |
| sm     | max-width: 640px  |
| md     | max-width: 768px  |
| lg     | max-width: 1024px |
| xl     | max-width: 1280px |
| 2xl    | max-width: 1536px |

## Spacing

### Pixel value

| value | equals         |
| ----- | -------------- |
| 0     | 0px            |
| px    | 1px            |
| 0.5   | 2px = 0.125rem |
| 1     | 4px = 0.25rem  |
| 1.5   | 6px = 0.375rem |
| 2     | 8px = 0.5rem   |

### [padding](https://tailwindcss.com/docs/padding)

| class          | translation                   |
| -------------- | ----------------------------- |
| p              | padding                       |
| pt, pb, pl, pr | padding-top/bottom/left/right |
| px             | padding-left + right          |
| py             | padding-top + bottom          |
| ps, pe         | padding-inline-start / end    |

### [margin](https://tailwindcss.com/docs/margin)

| class          | translation                  |
| -------------- | ---------------------------- |
| m              | margin                       |
| mt, mb, ml, mr | margin-top/bottom/left/right |
| mx             | margin-left + right          |
| my             | margin-top + bottom          |

### space

| class   | translation |
| ------- | ----------- |
| space-y | margin-top  |
| space-x | margin-left |
