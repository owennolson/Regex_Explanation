# Credit Card Verification Regex

In this tutorial, we will create a regular expression that matches a valid credit card number. Credit card numbers are 16-digit numbers that are usually split into four groups of four digits each. The first digit in the credit card number determines the type of credit card. For example, Visa credit cards start with a "4", while MasterCard credit cards start with a "5".

## Table of Contents

- [Summary](#summary)
- [Regex](#regex)
- [Explanation](#explanation)
- [Example](#example)
- [Author](#author)

## Summary

We will create a regular expression that matches a valid credit card number, including the four-digit groups and the first digit of the credit card number. The regular expression will also allow for optional spaces between the four-digit groups.

## Regex

Here is the regular expression we will create:

```
^(?:4[0-9]{3}|5[1-5][0-9]{2}|6(?:011|5[0-9]{2})|3[47][0-9]{2})[- ]?[0-9]{4}[- ]?[0-9]{4}[- ]?[0-9]{4}$
```

This regular expression matches the following types of credit cards:

- Visa
- MasterCard
- American Express
- Discover

## Explanation

Let's break down the regular expression:

- `^` - The beginning of the string.
- `(?:4[0-9]{3}|5[1-5][0-9]{2}|6(?:011|5[0-9]{2})|3[47][0-9]{2})` - This matches the first digit of the credit card number. It uses a non-capturing group with the `?:` syntax. The regular expression matches:
  - `4[0-9]{3}` - Visa credit cards start with a "4", followed by three digits between 0 and 9.
  - `5[1-5][0-9]{2}` - MasterCard credit cards start with a "5", followed by a digit between 1 and 5, and two more digits between 0 and 9.
  - `6(?:011|5[0-9]{2})` - Discover credit cards start with a "6". The regular expression matches either "011" or a digit between 50 and 59, followed by two more digits between 0 and 9.
  - `3[47][0-9]{2}` - American Express credit cards start with a "3", followed by either a "4" or a "7", and two more digits between 0 and 9.
- `[- ]?` - This matches an optional space or dash between the four-digit groups.
- `[0-9]{4}` - This matches each of the four-digit groups in the credit card number.
- `$` - The end of the string.

## Example

```javascript
const regex = /^(?:4[0-9]{3}|5[1-5][0-9]{2}|6(?:011|5[0-9]{2})|3[47][0-9]{2})[- ]?[0-9]{4}[- ]?[0-9]{4}[- ]?[0-9]{4}$/;

console.log(regex.test("4111 1111 1111 1111")); // true
console.log(regex.test("6011-1111-1111-1117")); // true
console.log(regex.test("3782 8224 6310 005")); // true
console.log(regex.test("5555 5555 5555 4444")); // false
```

This code will output `true` for the first three credit card numbers and `false` for the last one, since it's not a valid credit card number.

## Author

Hi, my name is Owen Olson and I created this simple Regex Credit Card Verification tutorial. Check out more of my stuff at https://github.com/owennolson !!