[![Chat](https://badges.gitter.im/chat.svg)](//gitter.im/lighterio/public)
[![Version](https://img.shields.io/npm/v/exam-is.svg)](//www.npmjs.com/package/exam-is)
[![Downloads](https://img.shields.io/npm/dm/exam-is.svg)](//www.npmjs.com/package/exam-is)
[![Build](https://img.shields.io/travis/lighterio/exam-is.svg)](//travis-ci.org/lighterio/exam-is)
[![Coverage](https://img.shields.io/coveralls/lighterio/exam-is/master.svg)](//coveralls.io/r/lighterio/exam-is)
[![Style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](//www.npmjs.com/package/standard)

`exam-is` is a fast JavaScript assertion library designed to be used with
[`exam`](https://github.com/lighterio/exam), or any test runner that knows
how to deal with an `AssertionError`.

## Installation
Install `exam-is` as a dev dependency:
```bash
npm install --save-dev exam-is
```

## API

You can use `is` methods to make assertions:
```js
var a = [1, 2, 3];
is.array(a);
is.same(a, [1,2,3]);
is.number(a[0]);
is.is(a[0], 1);
```

Each `is` method also returns `is` so you can chain, if that's your thing:
```js
var a = [1, 2, 3];
is
  .array(a)
  .same(a, [1,2,3])
  .number(a[0])
  .is(a[0], 1)
```

### Comparisons

#### is(actual, expected)
The `is.is` function is also known simply as `is`, allowing a shorthand strict
equality assertion.
```js
var one = 1;
is(one, 1);   // No error.
is(one, '1'); // Throws an AssertionError.
```

It asserts that `actual` is equal to `expected`, and that they are of the same
type.

#### is.not(actual, expected)
Asserts that `actual` is not equal to `expected` (or that they are not of the
same type).

#### is.equal(actual, expected)
Asserts that `actual` is equal to `expected`, within JavaScript's dynamic type
system.

#### is.notEqual(actual, expected)
Asserts that `actual` is **not** equal to `expected`, within JavaScript's
dynamic type system.

#### is.same(actual, expected) *or* is.deepEqual(actual, expected)
Asserts that `actual` is "the same" as `expected`, meaning that their
stringified representations are equal.

#### is.notSame(actual, expected) *or* is.notDeepEqual(actual, expected)
Asserts that `actual` is **not** "the same" as `expected`, meaning that their
stringified representations are unequal.

#### is.greater(first, second)
Asserts that the `first` value is greater than the `second`.

#### is.less(first, second)
Asserts that the `first` value is less than the `second`.

#### is.greaterOrEqual(first, second)
Asserts that the `first` value is greater than or equal to the `second`.

#### is.lessOrEqual(first, second)
Asserts that the `first` value is less than or equal to the `second`.

### Strict Type Checks

#### is.type(value, expectedType)
Asserts that the value is of the expected type, expressed as a case-sensitive
string returned by `typeof`.

```js
var num = 1;
var one = '1'
is.type(num, 'number'); // No error.
is.type(one, 'number'); // Throws an AssertionError.
is.type(num, 'Number'); // Throws an AssertionError.
is.type(one, 'string'); // No error.
```

#### is.notType(value, expectedType)
Asserts that the value is **not** of the expected type, expressed as a
case-sensitive string returned by `typeof`.

#### is.null(value)
Asserts that the value is null. This is a strictly-typed assertion.

#### is.notNull(value)
Asserts that the value is **not** null. This is a strictly-typed assertion.

#### is.undefined(value)
Asserts that the value is undefined. This is a strictly-typed assertion.

#### is.notUndefined(value) *or* is.defined(value)
Asserts that the value is **not** undefined. This is a strictly-typed
assertion.

#### is.boolean(value)
Asserts that the value is a boolean. This is a strictly-typed assertion, so
truthy or falsy values which are not actually `true` or `false` will fail this
assertion.

#### is.notBoolean(value)
Asserts that the value is **not** a boolean. This is a strictly-typed, so
`true` and `false` are the only values that will fail this assertion.

#### is.number(value)
Asserts that the value is a number value. This is a strictly-typed assertion,
so strings with numeric values will fail this assertion.

#### is.notNumber(value)
Asserts that the value is a number value. This is a strictly-typed assertion,
so numeric values are the only values that will fail this assertion.

#### is.string(value)
Asserts that the value is a string. This is a strictly-typed assertion.

#### is.notString(value)
Asserts that the value is **not** a string. This is a strictly-typed assertion.

#### is.function(value)
Asserts that the value is a function. This is a strictly-typed assertion.

#### is.notFunction(value)
Asserts that the value is **not** a function. This is a strictly-typed
assertion.

#### is.object(value)
Asserts that the value is an object. This is a strictly-typed assertion.

#### is.notObject(value)
Asserts that the value is **not** an object. This is a strictly-typed
assertion.

### Value Checks

#### is.true(value)
Asserts that the value is the boolean value `true`.

#### is.notTrue(value)
Asserts that the value is **not** the boolean value `true`.

#### is.false(value)
Asserts that the value is the boolean value `false`.

#### is.notFalse(value)
Asserts that the value is **not** the boolean value `false`.

#### is.truthy(value)
Asserts that the value evaluates to **true**, meaning the value is either
`true`, a non-zero number, a non-empty string, a function, or a non-null object.

#### is.falsy(value)
Asserts that the value evaluates to **false**, meaning the value is either
`false`, `0` (zero), `""` (empty string), `null`, `undefined` or `NaN`.

#### is.nan(value)
Asserts that the value cannot be evaluated as a number. This includes anything
that is not a number, a string representation of a number, `null` (which
evaluates to zero), `false` (which evaluates to zero) or a `Date` object.

#### is.notNan(value)
Asserts that the value **can** be evaluated as a number. This includes
numbers, a string representations of numbers, `null` (which
evaluates to zero), `false` (which evaluates to zero) and `Date` objects.

### Instance Checks

#### is.instanceOf(value, expectedClass)
Asserts that the value is an instance of the expected class.

#### is.notInstanceOf(value, expectedClass)
Asserts that the value is **not** an instance of the expected class.

#### is.array(value)
Asserts that the value is an instance of the `Array` class.

#### is.notArray(value)
Asserts that the value is **not** an instance of the `Array` class.

#### is.date(value)
Asserts that the value is an instance of the `Date` class.

#### is.notDate(value)
Asserts that the value is **not** an instance of the `Date` class.

#### is.error(value)
Asserts that the value is an instance of the `Error` class.

#### is.notError(value)
Asserts that the value is **not** an instance of the `Error` class.

#### is.regExp(value)
Asserts that the value is an instance of the `RegExp` class.

#### is.notRegExp(value)
Asserts that the value is **not** an instance of the `RegExp` class.

### Advanced

#### is.in(value, search)
Asserts that `value` is a string and that it contains a substring `search`
or matches a regular expression `search`.

#### is.notIn(value, search)
Asserts that either 1) `value` is not a string, 2) `search` is not
a string or regular expression, or 3) `search` is not found in `value`.

#### is.lengthOf(value, length)
Asserts that the value (string, array, etc.) has the specified length.

#### is.notLengthOf(value, length)
Asserts that the value (string, array, etc.) has no length, or a different
length than specified.

#### is.arrayOf(value, expectedTypeOrClass)
Asserts that the value is an array of the specified type or an array of
instances of the specified class (depending on whether the second argument
is a string).

#### is.notArrayOf(value, expectedTypeOrClass)
Asserts that the value is not an array, or contains an item that is not of the
specified type or an item that is not an instance of the specified class
(depending on whether the second argument is a string).

## More on exam-is...
* [Contributing](//github.com/lighterio/exam-is/blob/master/CONTRIBUTING.md)
* [License (ISC)](//github.com/lighterio/exam-is/blob/master/LICENSE.md)
* [Change Log](//github.com/lighterio/exam-is/blob/master/CHANGELOG.md)
* [Roadmap](//github.com/lighterio/exam-is/blob/master/ROADMAP.md)
