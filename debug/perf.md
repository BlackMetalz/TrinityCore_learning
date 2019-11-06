- Get a perf tool and run it while start world server

```
perf record ./worldserver
```

- after read it to see where is slows. File perf.data should be same directory while running this command
```
perf report
```
