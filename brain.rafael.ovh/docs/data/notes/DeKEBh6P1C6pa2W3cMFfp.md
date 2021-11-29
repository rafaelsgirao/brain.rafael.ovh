
This one seems tricky.

You're given NC access to interactive python with a message saying ```** import os and get a sh! should be easy ;) **```

First thing that crosses your mind is doing that. But you're greeted with an awful message:

```
>>> import os
Nope...
>>>
```

Turns out a lot of special keywords are filtered. A non exhaustive list of these:
```import, def, if, else, class, =, builtin, dict, ... and many others.```

[This post](https://lbarman.ch/blog/pyjail/) encouraged me to try to smash my keyboard and see what I could find. 

Some interesting things:
 -  any Error (e.g `ZeroDivisionError`, `ValueError`) is filtered to show up as just `Error` ;
 - Undefined things are spit out as `Error:  name 'x' is not defined`
 - Some keywords such as `pass`, `for` *don't* spit out as undefined
 - Typing a `\` on the prompt reveals `Error:  unexpected EOF while parsing (<string>, line 1)`
 - Typing `\\` on the prompt reveals `Error:  unexpected character after line continuation character (<string>, line 1)`

"This is a very long potato that doesn't fit" \
      "on a single line"

### TODO
```
>>> [x.func_code for x in [lambda: "test"]]
Result: [<code object <lambda> at 0x7fceed4797b0, file "<string>", line 1>]
>>>
```

Ideia: redefinir o `__class__` de uma função com o `_setattr__` para poder passar a ter uma classe
Ou então redefinir o __name__ para cenas

## External references used
- https://titanwolf.org/Network/Articles/Article?AID=fc8539b6-c4d1-4735-b60b-846d40bf8fa2
- https://book.hacktricks.xyz/misc/basic-python/bypass-python-sandboxes
- https://github.com/mahaloz/ctf-wiki-en/blob/master/docs/pwn/linux/sandbox/python-sandbox-escape.md
- https://lbarman.ch/blog/pyjail/
- https://nedbatchelder.com/blog/201302/finding_python_3_builtins.html
- https://stackoverflow.com/questions/13307110/can-you-recover-from-reassigning-builtins-in-python
- https://stackoverflow.com/questions/15404256/changing-the-class-of-a-python-object-casting

[x for x in [lambda: "test"]][0].func_code

[lambda: "teste"][0]

