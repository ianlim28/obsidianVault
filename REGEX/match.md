#match #gi #global #caseInsensitive

`gi` at the end of the regex means global and insensitive.
-  `g` stands for "global" and it allows the regular expression to match all occurrences of the pattern in the input string, rather than just the first one.
- `i` stands for "case insensitive" and it makes the regular expression match both uppercase and lowercase characters.

In the context of the `countVowels` function, the regular expression `/[aeiou]/gi` is used with the `match()` method to find all occurrences of the vowels 'a', 'e', 'i', 'o', and 'u' in the given string `subject`. The `.length` at the end of `.match(/[aeiou]/gi).length` returns the number of matches found, which represents the count of vowels in the string.

```js
function countVowels(subject) {
    return subject.match(/[aeiou]/gi).length;
}
```