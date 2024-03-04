# Godot Game
A simple template for creating a Godot game in C++ using GDExtension.

## Setup Windows
1. Install Visual Studio with Visual C++
2. Install Python 3 from https://www.python.org/. Make sure to add python executables to path.
3. Install scons via pip
```bash
$> pip install scons
```
4. In this repo update all submodules:
```bash
$> git submodule update --init --recursive
```
5. Build godot editor (this may take a while)
```bash
$> cd godot
$> scons platform=windows target=template_release
$> scons platform=windows target=editor
$> cd ..
```
6. Build godot-cpp wrapper
```bash
$> cd godot-cpp
$> scons platform=windows
$> cd ..
```
7. Open folder in VSCode with C++ Extension installed. Use the "Run" targets "Debug: Editor (Windows)" and "Debug: Game (Windows)" to build the code and run either the Editor or Game directly

## Setup Linux
TODO
