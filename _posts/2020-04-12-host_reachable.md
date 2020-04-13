# Python function to check if a host is reachable
(Tested on MacOS 10.15.3)

```python
import os

def host_is_reachable(host: str) -> bool:
  return True if os.system(f"ping -t 1 -o {host}") == 0 else False
```

Note: this is **not safe** if the `host` parameter will be coming from an untrusted user.

