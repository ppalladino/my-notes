# regex

Copying notes from: [https://www.codecademy.com/learn/introduction-to-regular-expressions/modules/intro-to-regex/cheatsheet](https://www.codecademy.com/learn/introduction-to-regular-expressions/modules/intro-to-regex/cheatsheet)

####

## Review

Do you feel those regular expression superpowers coursing through your body? Do you just want to scream `ah+` really loud? Awesome! You are now ready to take these skills and use them out in the wild. Before beginning your adventures, let’s review what we’ve learned.

* _Regular expressions_ are special sequences of characters that describe a pattern of text that is to be matched
* We can use _literals_ to match the exact characters that we desire
* _Alternation_, using the pipe symbol `|`, allows us to match the text preceding or following the `|`
* _Character sets_, denoted by a pair of brackets `[]`, let us match one character from a series of characters
* _Wildcards_, represented by the period or dot `.`, will match any single character (letter, number, symbol or whitespace)
* _Ranges_ allow us to specify a range of characters in which we can make a match
* _Shorthand character classes_ like `\w`, `\d` and `\s` represent the ranges representing word characters, digit characters, and whitespace characters, respectively
* _Groupings_, denoted with parentheses `()`, group parts of a regular expression together, and allows us to limit alternation to part of a regex
* _Fixed quantifiers_, represented with curly braces `{}`, let us indicate the exact quantity or a range of quantity of a character we wish to match
* _Optional quantifiers_, indicated by the question mark `?`, allow us to indicate a character in a regex is optional, or can appear either `0` times or `1` time
* The _Kleene star_, denoted with the asterisk `*`, is a quantifier that matches the preceding character `0` or more times
* The _Kleene plus_, denoted by the plus `+`, matches the preceding character `1` or more times
* The _anchor_ symbols hat `^` and dollar sign `$` are used to match text at the start and end of a string, respectively

## Detailed Review

#### Literals in Regular Expressions

In Regular expression, the `literals` are the simplest characters that will match the exact text of the literals. For example, the regex `monkey` will completely match the text `monkey` but will also match `monkey` in text `The monkeys like to eat bananas.`

#### Negation

Shorthand character classes simplify writing regular expressions. For example, `\w` represents the regex range `[A-Za-z0-9_]`, `\d` represents \[0-9], `\W` represents `[^A-Za-z0-9_]` matching any character not included by `\w`, `\D` represents `[^0-9]` matching any character not included by `\d`.

#### Alternation in Regular Expressions

Alternation indicated by the pipe symbol `|`, allows for the matching of either of two subexpressions. For example, the regex `baboons|gorillas` will match the text `baboons` as well as the text `gorillas`.

#### Character Sets in Regular Expressions

Regular expression character sets denoted by a pair of brackets `[]` will match any of the characters included within the brackets. For example, the regular expression `con[sc]en[sc]us` will match any of the spellings `consensus`, `concensus`, `consencus`, and `concencus`.

#### Wildcards in Regular expressions

In Regular expression, wildcards are denoted with the period `.` and it can match any single character (letter, number, symbol or whitespace) in a piece of text. For example, the regular expression `.........` will match the text `orangutan`, `marsupial`, or any other 9-character text.&#x20;

What happens if we want to match an actual period, `.`? We can use the escape character, `\`, to escape the wildcard functionality of the `.` and match an actual period. The regex `Howler monkeys are really lazy\.` will completely match the text `Howler monkeys are really lazy.`.

#### Regular Expression Ranges

Regular expression ranges are used to specify a range of characters that can be matched. Common regular expression ranges include: \[A-Z]. : match any uppercase letter \[a-z]. : match any lowercase letter \[0-9]. : match any digit \[A-Za-z] : match any uppercase or lowercase letter.

#### Shorthand Character Classes in Regular Expressions

Shorthand character classes simplify writing regular expressions. For example, `\w` represents the regex range `[A-Za-z0-9_]`, `\d` represents \[0-9], `\W` represents `[^A-Za-z0-9_]` matching any character not included by `\w`, `\D` represents `[^0-9]` matching any character not included by `\d`. [https://www.regular-expressions.info/shorthand.html](https://www.regular-expressions.info/shorthand.html)

#### Grouping in Regular Expressions

In Regular expressions, grouping is accomplished by open `(` and close parenthesis `)`. Thus the regular expression `I love (baboons|gorillas)` will match the text `I love baboons` as well as `I love gorillas`, as the grouping limits the reach of the `|` to the text within the parentheses.

#### Quantifiers - Fixed

Here’s where things start to get really interesting. So far we have only matched text on a character by character basis. But instead of writing the regex `\w\w\w\w\w\w\s\w\w\w\w\w\w`, which would match 6 word characters, followed by a whitespace character, and then followed by more 6 word characters, such as in the text `rhesus monkey`, is there a better way to denote the quantity of characters we want to match?

The answer is yes, with the help of quantifiers! _**Fixed quantifiers**_, denoted with curly braces `{}`, let us indicate the exact quantity of a character we wish to match, or allow us to provide a quantity range to match on.

* `\w{3}` will match _exactly_ 3 word characters
* `\w{4,7}` will match _at minimum_ 4 word characters and _at maximum_ 7 word characters

The regex `roa{3}r` will match the characters `ro` followed by `3` `a`s, and then the character `r`, such as in the text `roaaar`. The regex `roa{3,7}r` will match the characters `ro` followed by _at least_ `3` `a`s and _at most_ `7` `a`s, followed by an `r`, matching the strings `roaaar`, `roaaaaar` and `roaaaaaaar`.

#### Quantifiers - Optional

You are working on a research project that summarizes the findings of primate behavioral scientists from around the world. Of particular interest to you are the scientists’ observations of humor in chimpanzees, so you whip up some regex to find all occurrences of the word `humor` in the documents you have collected. To your dismay, your regex misses the observations of amusement written by scientists hailing from British English speaking countries, where the spelling of the word is `humour`. Optional quantifiers to the rescue!

_**Optional quantifiers**_, indicated by the question mark `?`, allow us to indicate a character in a regex is optional, or can appear either `0` times or `1` time. For example, the regex `humou?r` matches the characters `humo`, then either `0` occurrences or `1` occurrence of the letter `u`, and finally the letter `r`. Note the `?` _only_ applies to the character directly before it.

With all quantifiers, we can take advantage of grouping to make even more advanced regexes. The regex `The monkey ate a (rotten )?banana` will completely match both `The monkey ate a rotten banana` and `The monkey ate a banana`.

Since the `?` is a metacharacter, you need to use the escape character in your regex in order to match a question mark `?` in a piece of text. The regex `Aren't owl monkeys beautiful\?` will thus completely match the text `Aren't owl monkeys beautiful?`.

#### Quantifiers - 0 or More, 1 or More

In 1951, mathematician Stephen Cole Kleene developed a system to match patterns in written language with mathematical notation. This notation is now known as regular expressions!

In his honor, the next piece of regular expressions syntax we will learn is known as the Kleene star. The _**Kleene star**_, denoted with the asterisk `*`, is also a quantifier, and matches the preceding character `0` or more times. This means that the character doesn’t need to appear, can appear once, or can appear many many times.

The regex `meo*w` will match the characters `me`, followed by `0` or more `o`s, followed by a `w`. Thus the regex will match `mew`, `meow`, `meooow`, and `meoooooooooooow`.

Another useful quantifier is the _**Kleene plus**_, denoted by the plus `+`, which matches the preceding character `1` or more times.

The regex `meo+w` will match the characters `me`, followed by `1` or more `o`s, followed by a `w`. Thus the regex will match `meow`, `meooow`, and `meoooooooooooow`, but not match `mew`.

Like all the other metacharacters, in order to match the symbols `*` and `+`, you need to use the escape character in your regex. The regex `My cat is a \*` will completely match the text `My cat is a *`.

#### Anchors

When writing regular expressions, it’s useful to make the expression as specific as possible in order to ensure that we do not match unintended text. To aid in this mission of specificity, we can use the anchor metacharacters. The _**anchors**_ hat `^` and dollar sign `$` are used to match text at the start and the end of a string, respectively.

The regex `^Monkeys: my mortal enemy$` will completely match the text `Monkeys: my mortal enemy` but not match `Spider Monkeys: my mortal enemy in the wild` or `Squirrel Monkeys: my mortal enemy in the wild`. The `^` ensures that the matched text begins with `Monkeys`, and the `$` ensures the matched text ends with `enemy`.

Without the anchor tags, the regex `Monkeys: my mortal enemy` will match the text `Monkeys: my mortal enemy` in both `Spider Monkeys: my mortal enemy in the wild` and `Squirrel Monkeys: my mortal enemy in the wild`.

Once again, as with all other metacharacters, in order to match the symbols `^` and `$`, you need to use the escape character in your regex. The regex `My spider monkey has \$10\^6 in the bank` will completely match the text `My spider monkey has $10^6 in the bank`.
