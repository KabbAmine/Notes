> 29 juin 2016 10:58:27

# Tips

- `fc`          : Open & edit the last command using `$EDITOR`.
- `<C-x><C-e>`  : Same as above but open a new file.
- `if [[ str =~ ^regex$ ]]`
- `eval $var`
- `!!`          : Execute the last command

# Functions

- Return in a function
  ```sh
  fun Foo() {
    local variable='foo'
    echo $variable
  }

  foo=$(Foo)
  ```

- `local variable` to make it local to the function, can be used with `declare`: `local -A assoc_array`

# Arrays

- To declare an array:

```sh
array=(elem1 elem2)
declare -A assoc_array=(["key1"]="value1" ["key2"]="value2")
```

- To reference an element:

```sh
${array[0]}
${assoc_array["key"]}
```

- To reference all elements:

```sh
${array[@]}
${array[*]}
${assoc_array[@]}
${assoc_array[*]}
```

__P.S__: If the word is double-quoted, `${name[*]}` expands to a single word with the value of each array member separated by the first character of the `$IFS` variable, and `${name[@]}` expands each element of name to a separate word.

- To reference the keys of an associative array:

```sh
${!assoc_array[@]}
${!assoc_array[*]}
```

__P.S:__ The treatment when in double quotes is similar to the expansion of the special parameters `@` and `*` within double quotes.
