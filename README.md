# VEX PROS Cross-Project File Sharing

PROS: https://github.com/purduesigbots/pros

This repository contains an example set of PROS Projects that share source and header files. This is done through editing the common.mk and Makefile files in each PROS project. 

The source and header files in the common directory are included in the compilation for both PROS projects (bot1 and bot2). In addition, object (.o) and dependency (.d) files are written to the common directory, so you don't have to recompile the common source files when you switch projects.

This repo contains sample C and C++ source and header files: test.c and test.h for C, and test.cpp and test.hpp for C++.

**I HAVE NO CLUE IF THE CODE ACTUALLY WORKS. ALL I KNOW IS THAT IT COMPILES.**

## Rationale

As a VEX U competitor (at the time of publishing this repo) I've run into the issue of sharing code across the 2 robots my team built, but not always transferring fixes done on one robot's code to the other robot.

This was particularly annoying because many times I spent hours looking for issues only to figure out that I had the fix for the problem, I just hadn't copied it over from the other robot's code. 

In addition, this meant that I made a fair few commits on either robot's repository which were merely copying over changes.

What I've done here allows me to avoid this, as header and source files in the common directory are included in compilation for each project.

### Possible Alternatives

If I wanted to be lazy, I could have just used a `#include` to copy source files over instead of going through Makefile hell (I could simply add the header files using the provided `EXTRA_INCLUDE` make variable in common.mk). However, I felt that doing so was a very dirty solution, as I would be using `#include` for source files.

Alternatively, I could have added code in common.mk to copy over the files when I invoked `make`. However, that also felt dirty to me, as there would be copies of the shared source files in each project, which could be confusing.

## Methods

All of the changes in the PROS projects I made to get this to work are in the Makefile and common.mk for each PROS project.

I added comments in both the Makefile and common.mk. They should be rather easy to spot, as each comment starts and ends with:

```
#---------------------------------------------------------------------------------
```
I also put these wherever sections of code that I changed end.
