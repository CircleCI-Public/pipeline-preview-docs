# NOTE: THIS IS SPECULATIVE FOR FEEDBACK, NOT WORKING SOFTWARE

## Using complex conditions in `when`

You might want to compare equality, check a string against a regexp, or do
simple boolean logic inside a conditional. In a `when` stanza the condition is evaluated as a boolean, so if you use `<< parameters.foo >>` as the scalar value of the condition that will be cast to a boolean value using the truthiness rules. For more complex conditionals you may also provide a map
of a single key, from the set `["equals", "matches", "or", "and", and "not"]`,
and a single value: a list of arguments.

### equals

`equals` operates on any number of arguments, and checks that they are all
equal.

```
- when:
    condition:
      equals: ["<< parameters.foo >>", "bar"]
```

### matches
`matches` is a function of two arguments--a pattern and a string to match. The
pattern must match the entire string.

```
- when:
    condition:
      matches: ['\w+[\w\d]+', "<< parameters.foo >>"]
```

### boolean operators: or, and, not

`or` is a function of any number of arguments. If any are truthy,
conditional steps will run.

```
- when:
    condition:
      or: ["<< parameters.foo >>", "<< parameters.bar >>"]
```

`and` is a function of any number of arguments. If all are truthy,
the conditional steps will run.
```
- when:
    condition:
      and: ["<< parameters.foo >>", "<< parameters.bar >>"]
```

`not` is a function of a single argument. If the argument is truthy, the
conditional steps will run.

```
- when:
    condition:
      not: "<< parameters.foo >>"
```

### Combining Conditionals

You can also combine conditionals. The arguments to any of the conditional functions above can be other conditionals. For example:

```
- when:
    condition:
      and:
        - matches: ['\w+', "<< parameters.foo >>"]
        - matches: ['\d+', "<< parameters.bar >>"]
        - not: ["<< parameters.bang" >>]
    steps:
      - do stuff here
```