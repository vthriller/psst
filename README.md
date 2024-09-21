**PSSt** (short for *[PSS](https://en.wikipedia.org/wiki/Proportional_set_size) tree*) is a simple utility that shows memory usage for every process as well as their children, taking shared memory into account. `tmpfs` file systems, unreclaimable SLAB caches, amdgpu VRAM spillover, and `zram` devices are also reported.

Sample output:

```
     PSS    ∑ PSS    PID command or mount point
  159.0k    12.8G      1 init [3]
    5.5M     7.0G  19645 ├ urxvt
    1.4M     7.0G  19646 │ └ bash
    1.0G     7.0G  19649 │   └ /opt/firefox/firefox-bin --name firefox-bin
  860.5M   860.5M  19937 │     ├ /opt/firefox/firefox-bin ...
  859.4M   859.4M  19817 │     ├ /opt/firefox/firefox-bin ...
    ...      ...    ...  │     ├ (...skipped for brevity...)
    7.4M     7.4M  20137 │     └ /opt/firefox/firefox-bin ...
    1.0G     1.0G  tmpfs ├ /dev/shm
    ...      ...    ...  ├ ...
```

Use `-q` to use less accurate estimates (useful for systems with large number of processes).
