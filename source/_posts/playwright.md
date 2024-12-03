---
title: playwright
date: 2024-10-04 04:26:41
tags:
  - playwright
  - Typescript
  - Testing
categories: programming
---

## Setup and run [Playwright](https://playwright.dev/)

### Install playwright

```Powershell
npm init playwright@latest
```

### Run playwright in UI Mode

```Powershell
npx playwright test --ui
```

### Run test

npx playwright test `filename`.spec.ts --config=`config file name`.config.ts --workers=4 --retries=3 --project="mschromium" --trace on -g "(?=.\*zh_CN)" --headed

```Powershell
npx playwright test merchant-directory.spec.ts --config=playwright.monocart.config.ts --workers=4 --retries=3 --project="mschromium" --trace on -g "(?=.*zh_CN)" --headed
```

## Basic Syntax

test Describer - group tests

```Typescript
test.describe("GroupName", () => {
    test.beforeEach(async ({ page }) => {
    //reload target page for each test
    await page.goto("https://playwright.dev");
  });
  test("testName", async ({ page }) => {
  });
});
```

| Element Retriver        | Explaination                                                              | Example                                                                      |
| ----------------------- | ------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| page.locator()          | [React locator](https://playwright.dev/docs/other-locators#react-locator) | await page.locator('\_react=ComponentName[enabled=true])                     |
| page.locator()          | [xPath](https://playwright.dev/docs/other-locators#xpath-locator)         | await page.locator('//div[@class="className"]/div/a')                        |
|                         |                                                                           | await page.locator('..div[@class="className"][position()=3]')                |
|                         | xPath union                                                               | await page.locator('//span[contains(@class, 'keyword')] \| //div[@id='id']') |
| page.locator()          | id                                                                        | await page.locator('#targetId')                                              |
| page.locator()          | class name                                                                | await page.locator('.className > div > a')                                   |
| page.getByRole()        | role                                                                      | await page.getByRole('button', { name: 'Submit' })                           |
| page.getByText()        | text                                                                      | await page.getByText('Text')                                                 |
| page.getByLabel()       | label                                                                     | await page.getByLabel('Label')                                               |
| page.getByPlaceholder() | placeholder                                                               | await page.getByPlaceholder('Placeholder')                                   |
| page.getByAltText()     | alt text                                                                  | await page.getByAltText('AltText')                                           |
| page.getByTitle()       | title                                                                     | await page.getByTitle('Title')                                               |
| page.getByTestId()      | test id                                                                   | await page.getByTestId('TestId')                                             |
| locator.nth(index)      | get the i-th element under locator                                        | await page.locator('.className').nth(1)                                      |

### locator iteration

```Typescript
  // selectedBrand = xpath locator with multiple results

  let brands = new Set(); //in case you want to get value
  for (const item of await selectedBrand.all()) {
    if (item) brands.add(item.getAttribute("value"));
  }
```

### xPath Conditions

| Conditions                             | Explaination              | Example                                                                      |
| -------------------------------------- | ------------------------- | ---------------------------------------------------------------------------- |
| Raw xPath                              | start by // or .. is same | await page.locator('..div[@class="className"]')                              |
| followed by child                      |                           | await page.locator('//div[@class="className"]/div/a')                        |
| only select the nth child of same type |                           | await page.locator('//div[@class="className"]/div[1]')                       |
|                                        | xPath union               | await page.locator('//span[contains(@class, 'keyword')] \| //div[@id='id']') |
| page.locator()                         | id                        | await page.locator('#targetId')                                              |

## [Fixture](https://www.youtube.com/watch?v=2O7dyz6XO2s)

Create a custom `test` object which extend the original `test()` function from playwright

- setup duplicated action
- setup action after `use`

```
const myTest = test.extend({
  webApp: async({page},use) => {
    console.log('setup')
    await use(page)
    console.log('finished')
  }
})

myTest("Test Description", async ({webApp}) => {
  await expect(webApp.getByTestId("TestID")).toBeVisible() //action
})
```

What it does is: 'setup' > the action > 'finished'

For the predefined Fixture across multiple ts use,
`setup.ts`

```
const {test, expect} = require{"@playwright/test"}
const {ac, pw} = process.env // take login details from .env

exports.expect = expect // export the original expect from original playwright
exports.test = test.extends({
  webApp: async ({page},use)=>{
    // do all the login things here
    await use(page)
  },
})
```

and import the custom test and expect from other ts

```
const { test , expect } = require("./setup")
```
