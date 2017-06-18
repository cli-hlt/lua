This is Lua (5.3.4) with an added CMakeLists.txt file for building
with CMake.

There is nothing added to the original Lua source as obtained from
http://www.lua.org on order to ease upgrading to newer versions.
The CMakeLists.txt currently works on Mac OSX (my machine) and
probably on Linux (untested). It does not try to modify luaconf.h
based on CMake parameters.

Feel free to fork and improve if you want to.

#### License
Lua is licensed under the terms of the MIT license. See doc/readme.html for details.

All additions are are also licensed under the terms of the MIT license as given
below:

The MIT License (MIT)

Copyright (c) 2013 cli-hlt

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
