# Third-party components

The Windows release includes the complete license texts in `licenses/`. The source package retains them with each dependency in `vendor/`.

| Component | Version | License | Source |
| --- | --- | --- | --- |
| Dear ImGui | 1.91.9b | MIT | https://github.com/ocornut/imgui/tree/v1.91.9b |
| JSON for Modern C++ | 3.11.3 | MIT | https://github.com/nlohmann/json/tree/v3.11.3 |
| TinyXML-2 | 11.0.0 | zlib | https://github.com/leethomason/tinyxml2/tree/11.0.0 |
| Microsoft WebView2 SDK / static loader | 1.0.2903.40 | Microsoft BSD-style license and included notices | https://www.nuget.org/packages/Microsoft.Web.WebView2/1.0.2903.40 |
| C++/WinRT headers supplied by Windows SDK | 2.0.250303.5 in the tested SDK | MIT | https://github.com/microsoft/cppwinrt |

WebView2 Evergreen Runtime is supplied separately by Microsoft under its own terms. Windows system APIs and the MSVC runtime are used to build and run the application. No source code from other Roblox account-manager applications is included.

C++/WinRT headers are consumed from the installed Windows SDK rather than bundled here. Its license notice is retained in `vendor/cppwinrt/LICENSE` and the Windows release's `licenses/CPPWinRT-LICENSE.txt`.
