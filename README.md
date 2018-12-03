# SnippetsOfSorts [![GitHub license](https://img.shields.io/badge/license-GLWTPL-blue.svg)](https://github.com/me-shaon/GLWTPL/blob/master/NSFW_LICENSE) [![Coverage Status](https://img.shields.io/badge/coverage-100%25-yellow.svg)]() [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)]() [![first-timers-only Friendly](https://img.shields.io/badge/first--timers--only-friendly-blue.svg)](http://www.firsttimersonly.com/) [![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/SaadAAkash/Compiler-Linux-GIT-AWS-Essentials/graphs/commit-activity) [![Open Source Love svg1](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/) [![made-with-love](https://img.shields.io/badge/Made%20with-Love-1f425f.svg)](https://saadaakash.bitbucket.io/)
Scripts for boring stuffs. Snippets for teasing brain-cells. That's it.

## JavaScript

* Short-Circuit Evaluation 

```
var a;
var b = null;
var c = undefined;
var d = 4;
var e = 'five';

var f = a || b || c || d || e;

console.log(f);
```

Output:

```
4 // 6 falsy values in JS: false, 0, “” (empty string), null, undefined, NaN (Not A Number)
```

* == vs ===

```
3 === '3' // Output: false (Number compared to String) -> Strict Equality
3 == '3'  // Outpt: true -> Loose Equality: Allows to convert the values into a common type
```

* null, undefined and NaN :

```
null == null
undefined == undefined
null == undefined
//all returns true: null and undefined are only equal to themselves
NaN == null
NaN == undefined
NaN == NaN
// all returns false: 
NaN isn’t equivalent to anything (not even itself!):
```

## Python

* [CSV to JSON](https://github.com/Interspeed/CSVtoJSONPy)
* [HTTP Server One Liners](https://gist.github.com/SaadAAkash/d8e9ef3fcdd5040d1ba8981bdf43bab3)
* [YouTube Sentiment Analysis](https://github.com/realpython/python-scripts/blob/master/scripts/31_youtube_sentiment.py)
* [Some more interesting ones](https://github.com/realpython/python-scripts/)
