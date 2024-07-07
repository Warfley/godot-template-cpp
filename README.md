# Godot C++ Template
A simple template for creating a Godot game in C++ using GDExtension.

## Setup Windows
1. Install Visual Studio with Visual C++
2. Install Python 3 from https://www.python.org/. Make sure to add python executables to path.
3. Install scons via pip
```bash
$> pip install scons
```
4. Install godot 4.2 as godot.exe in system PATH. E.g. when building from source:
```bash
$> git clone -b 4.2 https://github.com/godotengine/godot.git "C:\godot"
$> cd "C:\godot"
$> scons platform=windows target=editor
$> cp "bin\godot.windows.editor.x86_64.exe" "bin\godot.exe"
# Now add C:\godot\bin to path to continue
```
5. In this repo update all submodules:
```bash
$> git submodule update --init --recursive
```
6. Build godot-cpp wrapper
```bash
$> cd godot-cpp
$> scons platform=windows
$> cd ..
```
7. Open folder in VSCode with C++ Extension installed. Use the "Run" targets "Debug: Editor (Windows)" and "Debug: Game (Windows)" to build the code and run either the Editor or Game directly

## Setup Linux
1. Install required software packages (see https://docs.godotengine.org/en/stable/contributing/development/compiling/compiling_for_linuxbsd.html)
2. Install godot 4.2 into /usr/local/bin. E.g. when building from source:
```bash
$> git clone -b 4.2 https://github.com/godotengine/godot.git /opt/godot
# Make sure you have write rights to access /opt/godot
$> cd /opt/godot
$> scons platform=linuxbsd target=editor
$> sudo ln -s /opt/godot/bin/godot.linuxbsd.editor.x86_64 /usr/local/bin/godot
```
3. In this repo update all submodules:
```bash
$> git submodule update --init --recursive
```
4. Build godot-cpp wrapper
```bash
$> cd godot-cpp
$> scons platform=linux
$> cd ..
```
5. Open folder in VSCode with C++ Extension installed. Use the "Run" targets "Debug: Editor" and "Debug: Game" to build the code and run either the Editor or Game directly