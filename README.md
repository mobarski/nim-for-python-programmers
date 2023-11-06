# Nim for Python Programmers

An assortment of code snippets designed to ease the transition from Python to Nim.

While similar in objective to the [Nim for Python Programmers guide](https://github.com/nim-lang/Nim/wiki/Nim-for-Python-Programmers) on the Nim language's official GitHub page, this collection focuses more on individual lines of code and their Nim equivalents.



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

| Python                     | Nim                        |
| -------------------------- | -------------------------- |
| `x = ["a", "b", "c"]`      | `var x = @["a", "b", "c"]` |
| `len(x)`                   | `x.len`                    |
| `for i,v in enumerate(x):` | `for i,v in x:`            |
| `if "a" in x:`             | `if "a" in x:`             |
| `x.append("z")`            | `x.add("z")`               |
| `x.insert(0,"!")`          | `x.insert("!",0)`          |
| `x[-1]`                    | `x[^1]`                    |
| `x[2:4]`                   | `x[2..3]`                  |



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
| `x["z"] += 9`                     | `x.inc("z",9)` <br />==doesn't work with "to_count_table" !!! why ???== |
| `for k,v in x.most_common():`     | TODO                                                         |



## sort

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
| f  = open(path, "w")      | TODO                      |
|                           |                           |



## f-string → strformat

| Python             | Nim                    |
| ------------------ | ---------------------- |
|                    | `import std/strformat` |
| `f"{k}"`           | `"{k}".fmt`            |
| `f"{v:0.3f}"`      | `"{v:0.3f}".fmt`       |
| `f"{100*x:0.1f}%"` | ` "{100*x:0.1f}%".fmt` |





## pickle → marshal

| Python                | Nim                                                        |
| --------------------- | ---------------------------------------------------------- |
| `import pickle`       | `import std/marshal`                                       |
| `y = pickle.dumps(x)` | `let y = $$x`                                              |
| `z = pickle.loads(y)` | `let z = to[seq[int]](y)` <br />==requires explicit type== |
| TODO pickle.load      | TODO                                                       |
| TODO pickle.dump      | TODO                                                       |



## json

| Python          | Nim               |
| --------------- | ----------------- |
| `import json`   | `import std/json` |
| `json.dumps(x)` | TODO              |
| `json.loads(x)` | `parse_json(x)`   |



## os.environ

| Python                           | Nim                          |
| -------------------------------- | ---------------------------- |
| `import os`                      | `import std/os`              |
| `for k,v in os.environ.items():` | `for k,v in os.env_pairs():` |
| `os.getenv("PATH")`              | `os.get_env("PATH")`         |
| `os.environ["x"] = "abc"`        | `os.put_env("x", "abc")`     |



## sys.argv

| Python       | Nim                        |
| ------------ | -------------------------- |
| `import sys` | `import os`                |
| `sys.argv`   | `os.command_line_params()` |



## multiprocessing -- TODO

| Python | Nim  |
| ------ | ---- |
|        |      |
|        |      |
|        |      |

