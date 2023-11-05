# Nim for Python Programmers

Collection of code snippets that compare Nim and Python.



## dict → Table

| Python                           | Nim                                     |
| -------------------------------- | --------------------------------------- |
|                                  | `import std/tables`                     |
| `x = {"a":11, "b":22}`           | `var x = {"a":11, "b":22}.to_table`     |
| `x = dict([("a",11), ("b",22)])` | `var x = [("a",11), ("b",22)].to_table` |
| `x = dict()`                     | `var x = init_table[string, int]()`     |
| `x["a"] = 11`                    | `x["a"] = 11`                           |
| `x.get("c",33)`                  | `x.get_or_default("c",33)`              |
| `if "b" in x:`                   | `if "b" in x:`                          |
| `for k in x:`                    | `for k in x.keys:`                      |
| `for k,v in x.items():`          | `for k,v in x.pairs:`                   |
| `del x["a"]`                     | `x.del("a")`                            |



## list → seq

| Python                | Nim                        |
| --------------------- | -------------------------- |
| `x = ["a", "b", "c"]` | `var x = @["a", "b", "c"]` |
| `len(x)`              | `x.len`                    |
| `if "a" in x:`        | `if "a" in x:`             |
| `x.append("z")`       | `x.add("z")`               |
| `x.insert(0,"!")`     | `x.insert("!",0)`          |



## set → HashSet

| Python              | Nim                                  |
| ------------------- | ------------------------------------ |
|                     | `import std/sets`                    |
| `x = {"a","b","c"}` | `var x = @["a","b","c"].to_hash_set` |
| `x = set()`         | `var x = init_hash_set[string]()`    |
| `x.add("a")`        | `x.incl("a")`                        |
| `x.remove("a")`     | `x.excl("a")`                        |
| `len(x)`            | `x.len`                              |



## Counter → CountTable

| Python                            | Nim                                                          |
| --------------------------------- | ------------------------------------------------------------ |
| `from collections import Counter` | `import std/tables`                                          |
| `x = Counter("abbaca")`           | `var x = "abbaca".to_count_table`                            |
| `x = Counter()`                   | `var x = init_count_table[string]()`                         |
| `x["z"] += 9`                     | `x.inc("z",9)` ==# doesn't work with "to_count_table" !!! why ???== |
| `for k,v in x.most_common():`     | TODO                                                         |



## sort → sort

| Python                        | Nim                    |
| ----------------------------- | ---------------------- |
|                               | `import std/algorithm` |
| `sorted([9,3,7,5])`           | `@[9,3,7,5].sorted`    |
| `x = [9,3,7,5]`               | `var x = @[9,3,7,5]`   |
| `x.sort()`                    | `x.sort`               |
| `x.sort(reverse=True)`        | `x.sort(Descending)`   |
| `y.sort(key=lambda x:x.name)` | TODO                   |



## open

| Python                    | Nim                       |
| ------------------------- | ------------------------- |
| `for line in open(path):` | `for line in lines path:` |
|                           |                           |
|                           |                           |



## pickle → marshal

| Python                | Nim                                                    |
| --------------------- | ------------------------------------------------------ |
| `import pickle`       | `import std/marshal`                                   |
| `y = pickle.dumps(x)` | `let y = $$x`                                          |
| `z = pickle.loads(y)` | `let z = to[seq[int]](y)` ==# requires explicit type== |
| TODO pickle.load      | TODO                                                   |
| TODO pickle.dump      | TODO                                                   |



## os.env

| Python                           | Nim                          |
| -------------------------------- | ---------------------------- |
| `import os`                      | `import std/os`              |
| `for k,v in os.environ.items():` | `for k,v in os.env_pairs():` |
| `os.getenv("PATH")`              | `os.get_env("PATH")`         |

## sys.argv

| Python       | Nim                        |
| ------------ | -------------------------- |
| `import sys` | `import os`                |
| `sys.argv`   | `os.command_line_params()` |
|              |                            |

