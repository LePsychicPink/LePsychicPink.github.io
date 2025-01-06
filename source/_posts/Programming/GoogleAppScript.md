---
title: Google App Script
tags:
  - Typescript
  - GoogleSpreadSheet
categories: programming
---

## SpreadsheetApp

| function       | example                                                |
| -------------- | ------------------------------------------------------ |
| getSheetByName | SpreadsheetApp.getActive().getSheetByName("sheetName") |

## onOpen()

Call functions when script is opened

### Create Menu item

```Typescript
  SpreadsheetApp.getUi().createMenu("Custom Filter")
    .addItem("Filter rows", "hideWeekEnd") // hideWeekEnd() is a function defined
    .addItem("Show all rows", "showAllRows") // showAllRows() is a function defined
    .addToUi();
```
