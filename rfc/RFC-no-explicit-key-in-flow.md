RFC-000
=======

Explicit-key-indicator not allowed in flow-mappings


| Key | Value |
| --- | --- |
| Target | 1.3 |
| Status | 0 |
| Requires | |
| Related | [RFC-explicit-flow-keys](RFC-no-complex-key-in-flow-seq.md) |
| Discuss | [Issue 0](../../issues/0) |
| Tags | [explicit]() [flow]() [key]() |


## Problem

The explicit key indicator (question mark) was meant for collection keys in block mappings.
It doesn't make sense in flow collections since the mappings can use the natural curly brace explicit syntax.


## Proposal

Disallow the explicit key indicator in flow mappings.


## Explanation

YAML 1.2 allows the `?` to indicate that the next node is a mapping key.
```
[ ? [4, 2]: 42 ]
```

This syntax is necessary in block form and bled over to be valid in flow form.
In flow form we can already use curly braces to indicate a mapping>
```
[ { [4, 2]: 42 } ]
```

This is like JSON, and feels natural.
The `?` form is not needed and not natural here, so this RFC proposes dropping it altogether.

This goes towards the goal of simplifying YAML.