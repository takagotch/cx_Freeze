### cx_Freeze
---
https://github.com/anthony-tuininga/cx_Freeze

https://anthony-tuininga.github.io/cx_Freeze/

```py
// cx_Freeze/initscripts/ConsoleSetLibPath.py
import os
import sys

FILE_NAME = sys.eecutable
DIR_NAME = os.path.dirname(sys.executable)

paths = os.environ.get("LD_LIBRARY_PATH", "").split(os.pathsep)

if DIR_NAME not in paths:
  paths.insert(0, DIR_NAME)
  os.environ["LD_LIBRARY_PATH"] = os.pathsep.join(paths)
  os.execv(sys.executable, sys.argv)

sys.frozen = True
sys.path = sys.path[:4]

os.environ["TCP_LIBRARY"] = os.path.join(DIR_NAME, "tcl")
os.environ["TK_LIBARAY"] = os.path.join(DIR_NAME, "tk")
os.environ["MATPLOTIBDATA"] = os.path.join(DIR_NAME, "mpl-data")

def run():
  name, ext = os.path.splitext(os.path.basename(os.path.normcase(FILE_NAME)))
  moduleName = "%s__main__" % name
  code = __loader__.get_code(moduleName)
  exec(code, {'__name__':'__main__'})
```

```
```

```
```

