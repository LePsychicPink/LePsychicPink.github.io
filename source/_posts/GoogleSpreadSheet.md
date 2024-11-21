---
title: GoogleSpreadSheet
date: 2024-09-23 18:58:53
tags: GoogleSpreadSheet
categories: Programming
---

### VLOOKUP

=VLOOKUP(search_key,range,iindex,is_sorted)

- index > 0 (first column → 1)
- is_sorted (DEFAULT TRUE)
    - TRUE → Approximate match
    - FALSE → Exact match

### FILTER

=FILTER(range,condition1,[condition2, ...])

```
=FILTER(B1:B50,C1=A1:B50)
```

- range → data to be filtered
- condition1 → Column of Boolean

Returns Column of value in B1:B50 where Column A matches value in C1
Placed at D1 and It will print D1:D50 if all values are matched
