---
id: 587d7b8a367417b2b2512b4c
title: >-
  分割代入で残余引数を使用して配列要素を割り当て直す
challengeType: 1
forumTopicId: 301218
dashedName: >-
  use-destructuring-assignment-with-the-rest-parameter-to-reassign-array-elements
---

# --description--

配列の分割において、残りの要素を別の配列にまとめたいことがあります。

次に示すように、`Array.prototype.slice()` に似た結果になります。

```js
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b);
console.log(arr);
```

コンソールには、値 `1, 2` と `[3, 4, 5, 7]` が表示されます。

変数 `a` と `b` は配列の最初と 2 番目の値を受け取ります。 その後は残余引数になっているため、`arr` は残りの値を配列の形で受け取ります。 残余引数は、リスト内の最後の変数としてのみ正しく動作します。 したがって、残余引数を使用して元の配列の最後の要素を取り除いた部分配列を取得することはできません。

# --instructions--

Use a destructuring assignment with the rest parameter to emulate the behavior of `Array.prototype.slice()`. `removeFirstTwo()` should return a sub-array of the original array `list` with the first two elements omitted.

# --hints--

`removeFirstTwo([1, 2, 3, 4, 5])` should be `[3, 4, 5]`

```js
const testArr_ = [1, 2, 3, 4, 5];
const testArrWORemoved_ = removeFirstTwo(testArr_);
assert(testArrWORemoved_.every((e, i) => e === i + 3) && testArrWORemoved_.length === 3);
```

`removeFirstTwo()` should not modify `list`

```js
const testArr_ = [1, 2, 3, 4, 5];
const testArrWORemoved_ = removeFirstTwo(testArr_);
assert(testArr_.every((e, i) => e === i + 1) && testArr_.length === 5);
```

`Array.slice()` は使用しないでください。

```js
(getUserInput) => assert(!getUserInput('index').match(/slice/g));
```

`list` の分割を使用する必要があります。

```js
assert(
  __helpers
    .removeWhiteSpace(code)
    .match(/\[(([_$a-z]\w*)?,){1,}\.\.\.shorterList\]=list/i)
);
```

# --seed--

## --seed-contents--

```js
function removeFirstTwo(list) {
  // Only change code below this line
  const shorterList = list; // Change this line
  // Only change code above this line
  return shorterList;
}

const source = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const sourceWithoutFirstTwo = removeFirstTwo(source);
```

# --solutions--

```js
function removeFirstTwo(list) {
  const [, , ...shorterList] = list;
  return shorterList;
}

const source = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const sourceWithoutFirstTwo = removeFirstTwo(source);
```
