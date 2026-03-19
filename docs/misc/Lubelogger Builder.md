# LubeLogger Builder

LubeLogger Builder is a cross-platform tool used for building and packaging LubeLogger so that it can be ran bare-metal on Windows, MacOS, and Linux.

[GitHub](https://github.com/hargata/lubelog_builder)

## Dev Notes

This is an internal tool used for publishing the Windows standalone executable of LubeLogger, no support will be provided for this tool. Users of this tool are expected to troubleshoot, debug, and modify the app for their use case. Any GitHub Issues submitted for this tool will be ignored.

No executable will be provided within the repo as the user is expected to have .NET 8 SDK installed on their machine so that they can build the repo themselves.

## Build and Run the Builder

1. Download the source code(can be found under Releases) and run `dotnet build`
2. The binary can be found in the `/bin/Debug/` folder 

## Building for Windows and Linux

It is recommended that you run the tool in Windows because it's the only environment we tested this tool in. You cannot target MacOS with the build tool in Windows, it won't compile right despite generating an output, see below.

1. Download the source for the latest LubeLogger release
2. Extract the zip file
3. Run the Builder Tool
4. Select the folder containing the contents of the extracted zip file
5. Select Windows and Linux for the Target Architectures
6. Make sure `cmd.exe` is selected under Build Using
7. Click Build
8. The output zip file can be found in the source folder.

## Building for MacOS(>=12.x/Monterey only)

To build for MacOS you have to build and run the tool in MacOS.

[Video Walkthrough](https://www.youtube.com/watch?v=YWG0auL1x9o)

1. Download the source for the latest LubeLogger release
2. Extract the zip file
3. Run the Builder Tool
4. Select the folder containing the contents of the extracted zip file
5. Select MacOS for the Target Architectures
6. Make sure `zsh` is selected under Build Using
7. Click Build
8. The output zip file can be found in the source folder.
