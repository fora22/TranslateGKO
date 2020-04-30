# **PYTHON: REGULAR EXPRESSION**

Regular expression is a domain specific language (DSL) for string manipulation. Regular expression is not Python-exclusive feature, and is utilized by other programming languages as well (aka. regex).

## `re` Module

The module which allows Python to access regular expressions. To use the regular expression, place the letter `r` before the string object which indicates raw string.

| SYNTAX | EXAMPLE     | DESCRIPTION        |
| ------ | ----------- | ------------------ |
| `r`    | `r"string"` | Raw string object. |

### Special Sequences

In regular expression not only the backslash works as an escape character `\` but also as a metacharacter that supports various features.

| SYNTAX | EXAMPLE | DESCRIPTION                                      |
| ------ | ------- | ------------------------------------------------ |
| `\`    | `r"\"`  | Metacharacter for special sequence (+ *escaper*) |


## Grouping

Grouping makes series of characters or strings to be as one and allows grouped to become an argument for other metacharacters as seen in example of the previous section.

| OPERATION  | EXAMPLE                | DESCRIPTION                                      |
| ---------- | ---------------------- | ------------------------------------------------ |
| `()`       | `r"^str0(str1)" `      | Grouping `str1`  separately from `str0` .        |
| `group()`  | `re.search.group(...)` | Method used for calling a grouped.               |
| `groups()` | `re.search.groups( )`  | Method used for calling all the groups in tuple. |

Calling `group(0)` is same as `group()` which returns matched characters or strings between compared two. The rest of integer starting from 1 calls individual group starting from left to right and outer to inner group.

### Named Groups

Group can be specified to have its own name to be called. No double quotations are needed when inserting name but are needed when calling the named groups.

| SYNTAX | EXAMPLE                | DESCRIPTION                            |
| ------ | ---------------------- | -------------------------------------- |
| `?P<>` | `r"(?P<name>string)" ` | Designate group with name for calling. |

### Non-capturing Groups

Group that cannot be accessible by `group(...)` and `groups()` methods, which results skipping index on such groups. However, `group(0)` is an exception where it calls matched comparison between two rather than groups.

| SYNTAX | EXAMPLE          | DESCRIPTION                                             |
| ------ | ---------------- | ------------------------------------------------------- |
| `?:`   | `r"(?:string)" ` | Inaccessible via `group(...)`  and `groups()`  methods. |