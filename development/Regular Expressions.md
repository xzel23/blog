# Regular Expressions

## Predefined Character classes

|Construct|Description|
|---|---|
|.|Any character (may or may not match line terminators)|
|\d|A digit: [0-9]|
|\D|A non-digit: [^0-9]|
|\s|A whitespace character: [ \t\n\x0B\f\r]|
|\S|A non-whitespace character: [^\s]|
|\w|A word character: [a-zA-Z_0-9]|
|\W|A non-word character: [^\w]|

Source: [The Java™ Tutorials](https://docs.oracle.com/javase/tutorial/essential/regex/pre_char_classes.html)

## Capturing groups

Capturing groups in Java regex are defined by parenthesis. Capturing groups are numbered starting from one and can be accessed using the `Matcher.group(int)` method.

Alternatively, capturing groups can be given names by adding `?<name>` directly after the opening parenthesis.

**A Regex for parsing font-size declarations in CSS**

```
    (?<number>[\\d]+(\\.\\d+)?)(?<unit>[a-z%]+)
```

This regular expression consists of two named capturing groups, `number` and `unit`.

 - **`number`:** One or more digits, optionally followed by a dot and more digits.
 - **`unit`:** any number of letters or procent signs

In code this looks like this:

```
    Pattern pattern = Pattern.compile("(?<number>([\\d]+(\\.\\d+)?))(?<unit>[a-z%]+)");
    Matcher matcher = pattern.matcher(input);
    if (matcher.matches() {
        String number = matcher.group("number");
        String unit = matcher.group("unit");
        ...
    }
```

For the input String `1.2em` you will get these results:

|expression|value|
|---|---|
|input|`"1.2em"`|
|matcher.matches()|`true`|
|number|`"1.2"`|
|unit|`"em"`|

## Tools

 * [Online Test](https://www.freeformatter.com/java-regex-tester.html) for Regular Expressions