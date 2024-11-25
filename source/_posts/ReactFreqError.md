---
title: Frequent Error for React
date: 2024-09-14 01:27:25
tags: React
categories: programming
---

### ENOENT: no such file or directory

{% asset_img error1.png %}

Solution

```PowerShell
rm package-lock.json && npm i
```

### Sth requires a peer of other package but none is installed

```PowerShell
npm install --save-dev the other package
```
