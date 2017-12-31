---
title:  "On try/catch statements, and the optional-ness of the catch binding"
date:   2017-12-31 16:05:23
categories: [javascript]
tags: [thoughts, technology, typescript, tc39, esnext, try, catch, javascript]
---

It's been [proposed][PROPOSAL] that the `catch` portion of the Javascript `try`/`catch` statament no longer require a binding to the runtime `Error` object.

Instead of this
```js
try {
    // ... some risky business
} catch (error) {
    //   ^^^^^ Useless binding which everyone seceretly hates apparently
}
```

one can write this
```js
try {
    // ... some risky business
} catch {
    // error unfriended
}
```

Binding, no binding... it's a non-issue as far as I'm concerned. But I will say this: If you're working through my code, you won't find any `try`/`catch` statements, because the `try`-ing part **_is implied_**. 

I just write
```js
// ... some risky business
```
and move on. To accomodate _my_ programming style, I'm submitting the following proposal to TC39
```js
// ... some risky business
catch (error) {
    // fix stuff here
}
```

And for the record, I'm also fine with this
```js
// ... some risky business
catch {
    // fix stuff here
}
```

[PROPOSAL]: https://github.com/tc39/proposal-optional-catch-binding