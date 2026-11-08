# Cpp make project template
This is just a template repo so i dont have to remake the same makefile for most of my smallish cpp projects. It (should) work on both windows and unix systems.\
Basically a zig init template but for cpp. Might make a init tool similar to go modules that uses this as a base.
## Deps
```
make zig
```
It specifically needs GNU make since the wildcard call is not part of the normal make syntax.\
Its an odd combi ik but on most of my machines i have zig installed so it just works for me.\
I could use the zig build system but im more comfortable with makefiles than zig build and if i ever use this on a machine without zig it makes it easier to swap to other compilers.\
This will probably be swapped to g++ at somepoint since its the more suited choice.