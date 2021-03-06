---
title: ESLint
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->
# Disallow Labeled Statements (no-labels)

Labeled statements in JavaScript are used in conjunction with `break` and `continue` to control flow around multiple loops. For example:

```js
outer:
    while (true) {

        while (true) {
            break outer;
        }
    }
```

The `break outer` statement ensures that this code will not result in an infinite loop because control is returned to the next statement after the `outer` label was applied. If this statement was changed to be just `break`, control would flow back to the outer `while` statement and an infinite loop would result.

While convenient in some cases, labels tend to be used only rarely and are frowned upon by some as a remedial form of flow control that is more error prone and harder to understand.

## Rule Details

This rule aims to eliminate the use of labeled statements in JavaScript. It will warn whenever a labeled statement is encountered and whenever `break` or `continue` are used with a label.

The following patterns are considered warnings:

```js
label:
    while(true) {
        // ...
    }

label:
    while(true) {
        break label;
    }

label:
    while(true) {
        continue label;
    }
```

The following patterns are not warnings:

```js
var f = {
    label: "foo"
};

while (true) {
    break;
}

while (true) {
    continue;
}

```

## When Not To Use It

If you need to use labeled statements, then you can safely disable this rule.

## Version

This rule was introduced in ESLint 0.4.0.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-labels.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-labels.md)
