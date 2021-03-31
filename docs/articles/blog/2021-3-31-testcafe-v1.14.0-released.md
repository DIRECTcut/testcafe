---
layout: post
title: TestCafe v1.14.0 Released
permalink: /blog/:title.html
---
# TestCafe v1.14.0 Released

This release brings scroll actions and a bugfix.

<!--more-->

## Enhancements

### ⚙ Scroll Actions ([PR #6066](https://github.com/DevExpress/testcafe/pull/6066))

When TestCafe interacts with elements on the page, it scrolls the page automatically to reach those elements.

This release introduces actions that allow you to manually scroll the webpage and its elements.

* [t.scroll](../documentation/reference/test-api/testcontroller/scroll.md) - scrolls the element to a specified position
* [t.scrollBy](../documentation/reference/test-api/testcontroller/scrollBy.md) - scrolls the element by the specified number of pixels
* [t.scrollIntoView](../documentation/reference/test-api/testcontroller/scrollintoview.md) - scrolls the element into view

You can use the `t.scroll` action to scroll an element to a position:

```js
 import { Selector } from 'testcafe';

 fixture`Scroll Action`
     .page('http://example.com');

 test('Scroll the container', async t => {
     const container = Selector('#container');

     await t
         .scroll(container, 'bottomRight')
 });
 ```

 `t.scrollBy` allows you to scroll an element (or the webpage) by a set amount of pixels. The example below scrolls the webpage 200px up and 500px to the right:

 ```js
 import 'testcafe'

 fixture`Scroll Action`
     .page('http://example.com');

 test('Scroll the webpage', async t => {
     await t
         .scrollBy(500, -200)
 });
 ```

Use `t.scrollIntoView` to scroll an element into view:

```js
 import { Selector } from 'testcafe';

 fixture `Scroll Actions`
     .page `http://www.example.com/`;

 test('Scroll element into view', async t => {
     const target = Selector('#target')

     await t
         .scrollIntoView(target)
 });
 ```

## Bug Fixes

* Fixed an error that caused [expect.contains](../documentation/reference/test-api/testcontroller/expect/contains.md) assertions to display `undefined` for one of the passed string values in diffs ([#5473](https://github.com/DevExpress/testcafe/issues/5473))
