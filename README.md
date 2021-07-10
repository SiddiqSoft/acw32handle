Auto Closing/Releasing Win32 Handle Objects
-------------------------------------------

[![CodeQL](https://github.com/SiddiqSoft/acw32handle/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/SiddiqSoft/acw32handle/actions/workflows/codeql-analysis.yml)
[![Build Status](https://dev.azure.com/siddiqsoft/siddiqsoft/_apis/build/status/SiddiqSoft.acw32handle?branchName=main)](https://dev.azure.com/siddiqsoft/siddiqsoft/_build/latest?definitionId=4&branchName=main)
![](https://img.shields.io/nuget/v/SiddiqSoft.acw32h)
![](https://img.shields.io/github/v/tag/SiddiqSoft/acw32handle)
![](https://img.shields.io/azure-devops/tests/siddiqsoft/siddiqsoft/4)
![](https://img.shields.io/azure-devops/coverage/siddiqsoft/siddiqsoft/4)

# Objective
Make it easy to track the Win32 `HANDLE` and `HINTERNET` objects while keeping their use as drop-in replacement for their respective `HANDLE` or `HINTERNET` objects.
Use only when you're holding objects that your application is required to close/release.

# Requirements
- C++17
- Useful for Windows projects

# Usage

- Use the nuget [SiddiqSoft.acw32h](https://www.nuget.org/packages/SiddiqSoft.acw32h/)
- You can also git submodule: `git submodule add https://github.com/SiddiqSoft/acw32handle.git`

Example (when using nuget to add the header in the solution)

```cpp
#include <windows.h>
#include "siddiqsoft/acw32h.hpp"

void foo()
{
   // Use the object
   siddiqsoft::acw32h<HANDLE> h( ::CreateFileA(...));

   // or
   HANDLE mh = ::CreateFile(.....);
   // A std::move is required since the implementation requires
   // the transfer of ownership in order to close the handle.
   ACW32HANDLE myHandle( std::move(mh) );

   // Use and don't worry about any throw, exit; C++ will cleanup the handle if it was properly allocated!
}

```

<small align="right">

&copy; 2020 Siddiq Software LLC. All rights reserved. Refer to [LICENSE](LICENSE).

</small>
