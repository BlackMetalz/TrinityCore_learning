- Valgrind info: Valgrind has several tools/modes.
The default tool is Memcheck and should be the most useful for Trinity.

- Memcheck
Memcheck is a memory error detector. Memcheck can detect a lot of things.

You should start your core by this command:

```
valgrind --tool=memcheck --leak-check=full --log-file=valgrind.log ./worldserver
```

Note that: Your core become so slow(core startup 3-5mins+) and lost a lot of performance, so don't try to use it with a lot of players.

If you do a ctrl-c your log file should contains a lot of information. Most of them are "useless", like:
```
==22709== Conditional jump or move depends on uninitialised value(s)
==22709==    at 0x401707D: (within /lib/ld-2.10.1.so)
==22709==    by 0x40052C0: (within /lib/ld-2.10.1.so)
==22709==    by 0x4007FFA: (within /lib/ld-2.10.1.so)
==22709==    by 0x400361C: (within /lib/ld-2.10.1.so)
==22709==    by 0x40153E6: (within /lib/ld-2.10.1.so)
==22709==    by 0x400138C: (within /lib/ld-2.10.1.so)
==22709==    by 0x4000AF7: (within /lib/ld-2.10.1.so)
```
The number(22709) is the core's process id(PID).
The log file has a summary part at the end of the log:

```
==22709== LEAK SUMMARY:
==22709==    definitely lost: 1,308,624 bytes in 183,502 blocks.
==22709==    indirectly lost: 2,960 bytes in 31 blocks.
==22709==      possibly lost: 49,368 bytes in 1,088 blocks.
==22709==    still reachable: 69,714,748 bytes in 188,424 blocks.
==22709==         suppressed: 0 bytes in 0 blocks.
```

The "definitely lost" is a 99.9% memory leak, eg.:

```
==22709== 360 bytes in 1 blocks are definitely lost in loss record 1,203 of 1,396
==22709==    at 0x4C2626C: operator new(unsigned long) (vg_replace_malloc.c:230)
==22709==    by 0xB65316: OutdoorPvPTF::SetupOutdoorPvP() (OutdoorPvPTF.cpp:228)
==22709==    by 0xB5DBCC: OutdoorPvPMgr::InitOutdoorPvP() (OutdoorPvPMgr.cpp:79)
==22709==    by 0xCF8912: World::SetInitialWorldSettings() (World.cpp:1661)
==22709==    by 0x8F4606: Master::Run() (Master.cpp:234)
==22709==    by 0x8F3B35: main (Main.cpp:154)
```

Ref: 
https://trinitycore.atlassian.net/wiki/spaces/tc/pages/2130194/Valgrind
http://valgrind.org/docs/manual/quick-start.html#quick-start.interpret
