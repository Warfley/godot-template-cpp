#!/usr/bin/env python
import os
import sys
import glob as glob_2

LIB_NAME="libgame"
LIB_DIR="project/bin"

# SCons is really great:
# If BUILD_DIR is different we don't have build artifacts in our source
# But then the debugger works on the build directory, meaning changes are non persistent
# As this is more annyoing than build artifacts in the source, we keep it the same
BUILD_DIR="src"
SRC_DIR="src"

if BUILD_DIR != SRC_DIR:
    VariantDir(BUILD_DIR, SRC_DIR)

env = SConscript("godot-cpp/SConstruct")

# Because scons does not know how to do recursion, we must implement it our selves
folders = []
sources = Glob(BUILD_DIR + "/*.cpp")
for dir in glob_2.glob(SRC_DIR + "/**/"):
    folder = BUILD_DIR + dir[3:-1]
    folders.append(folder)
    sub_sources = Glob(folder + "/*.cpp")
    sources.extend(sub_sources)

# For the reference:
# - CCFLAGS are compilation flags shared between C and C++
# - CFLAGS are for C-specific compilation flags
# - CXXFLAGS are for C++-specific compilation flags
# - CPPFLAGS are for pre-processor flags
# - CPPDEFINES are for pre-processor defines
# - LINKFLAGS are for linking flags

env.Append(CPPPATH=folders)

if env["platform"] == "macos":
    lib_ext = ".{}.{}.framework/libgame.{}.{}".format(
            env["platform"], env["target"], env["platform"], env["target"]
        ),
elif env["platform"] == "ios":
    if env["ios_simulator"]:
        lib_ext = ".{}.{}.simulator.a".format(env["platform"], env["target"])
    else:
        lib_ext = ".{}.{}.a".format(env["platform"], env["target"])
else:
    lib_ext = env["suffix"] + env["SHLIBSUFFIX"]

lib_file = LIB_DIR + "/" + LIB_NAME + lib_ext

library = env.StaticLibrary(lib_file, source=sources) if env["platform"] == "ios" \
else env.SharedLibrary(lib_file, source=sources)

Default(library)
