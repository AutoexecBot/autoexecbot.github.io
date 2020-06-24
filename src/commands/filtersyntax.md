# Filter Syntax

AutoexecBot provides a special syntax for matching names, words, and phrases in chat that allows for some flexibility in what gets matched.  These filters are always case-insensitive.  There's several available operators for constructing a filter.  This section explains those operators and their usage.

> ⚠ Currently the filter syntax will only match on words as it does not currently support spaces.  The ability to match on broader phrases, including spaces may be added in the future.

## Wildcard - Zero or more

It is possible to match on a wildcard in text zero or more times using the `*` operator.  This operator acts as a placeholder for any character repeated zero or more times.

### Example 1
> `KEK*`

This would match on any text that starts with `KEK`.  Such was `KEK`, `KEKW`, `KEKWW`, etc.  

### Example 2
> `KE*K`

This would match on any text that begins with `KE` and ends with `K` such as `KEK`, `KEEK`, `KEEKK`, etc.

## Wildcard - One or more

It is possible to match on a wildcard in text one or more times using the `+` operator.  This operator acts as a placeholder for any character repeated one or more times.

### Example 1
> KEK+

This would match on any text that starts with `KEK` and is followed by one or more characters. Such as `KEKW`, `KEKA`, `KEKAA`, `KEKWA`, etc.

### Example 2
> KE+K

This would match on any text that starts with `KE` followed by any character and the letter `K`.  Such as `KEEK`, `KEKK`, `KEKEK`, etc.

## Wildcard - At most one

It is possible to match on at most one wild card value using the `?` operator.  It is a placeholder for any character used zero to one times.

### Example 1
> `KEK?`

This would match on any text starting with `KEK` followed by zero to one more letter.  Such as `KEK`, `KEKA`, `KEKB`, `KEKC`, etc.

### Example 2
> `KE?K`

This would match any text that starts with `KEK`, followed by zero or one character and the letter `K`.  Such as `KEK`, `KEKK`, `KESK`, etc.

## Fuzzy letter match

It is a common case where users will use the letter `i` and letter `l` interchangably with the casing changed, due to their similar appearance under some fonts.  To help with this issue a special "fuzzy letter match" is provided for this case.  The `[i]` operator will match either the letter `i` or letter `l`.

### Example
> `boo[i]i`.

This would match either `booli` or `booii`.

## Repeating

Sometimes users will repeat the same character multiple times in order to circumvent filters.  To help with this, the repeating operator `%` can be used to indicate that the following character (including the fuzzy letter match) can be repeated one or more times.

### Example 1
> `KEK%W`

This would match `KEKW`, `KEKWW`, `KEKWWW`, etc.

### Example 2
> `bool%[i]`

This would match `booli`, `booll`, `boolii`, `boolll`, `boolli`, etc.

## Operator escape sequences

Sometimes it is necessary to filter on the characters listed as operators in this document verbatim and not as the operators themselves.  The filter syntax provides escape sequences prefixed with `\` to match on those characters reserved as operators. The following is a comprehensive list of escape sequences.

* `\\` - Matches on the character `\`
* `\*` - Matches on the character `*`
* `\+` - Matches on the character `+`
* `\?` - Matches on the character `?`
* `\%` - Matches on the character `%`
* `\[` - Matches on the character `[`
    - Prefixing `[i]` with `\` such as `\[i]` would match `[i]` exactly and not use the fuzzy match operator

> ⚠ Currently there is no way to escape the sequence `r#` at the beggining of a filter.  This will be corrected in a future update.

## Regular Expressions

> ⚠ This is a feature for advanced users only! Improper use can lead to unintended consequences, such as all users being banned from your channel. **USE AT YOUR OWN RISK**.  If you do not know what a regular expression is, this feature is probably not for you.

Prexifing any filter with `r#` will parse all text after the `r#` as a regular expression, following the syntax outlined in the Rust [regex crate](https://docs.rs/regex/latest/regex/) documentation.

### Example 1
> r#(a|b)+

This would match all text that's any combination of the letters `a` and `b` repeated one or more times.  Such as `a`, `b`, `ab`, `ba`, `aa`, `bb`, etc.