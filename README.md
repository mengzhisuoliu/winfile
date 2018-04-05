# Windows File Manager (WinFile)

The Windows File Manager lives again and runs on all currently supported version of Windows,
including Windows 10.  I welcome your thoughts, comments and suggestions.  There are two
versions of the source code in two branches:

1. original_plus: contains the source for WinFile as of Windows NT4 with minimal changes
so that it compiles with Visual Studio and runs on current Windows.

2. master: contains my personal changes / additions to WinFile.

I will consider bugs fixes and suggestions for minor changes to the master branch.  Feel free
to create a pull request or post issues as you see fit.

I will not be changing the original_plus branch nor creating other branches for other purposes.
You are welcome do that on your own.

## History

The Windows File manager was originally released with Windows 3.0 in the early 1990s.  You
can read more about the history at https://en.wikipedia.org/wiki/File_Manager_(Windows).

## Changes in original_plus

The source code provided here was copied from the Windows NT 4 source tree in November
2007.  The branch named original_plus contains a very limited set of  modifications
from the original sources to enable WinFile.exe to run on current Windows.
The most significant changes are:

1. converted to Visual Studio solution; works on VS 2015 and 2017
2. compiles and runs on 64-bit Windows (e.g., GetWindowLong -> GetWindowLongPtr, LONG -> LPARAM)
3. added a few header files which were stored elsewhere in the NT source tree (e.g., wfext.h)
4. deleted some unused files (e.g., winfile.def)
5. converted 64-bit arithmetic from internal libraries to C
6. converted internal shell APIs to public APIs (the primary reason the old version would not run)

## Changes in master v10.0 after original_plus

The master branch contains changes I have made since 2007.  The changes have been solely determined
by my needs and personal use.  Some of the changes have limitations that fit the way I use the tool.
For example, the path index which supports the new goto command only contains information for the c: drive.

I have also not redesigned or restructured WinFile in any major way.

Version v10.0 represents the entire set of changes from Nov. 2007 until this OSS project
was created.  For changes post v10.0, see the commit and release history.

In summary v10.0 has the following changes/new features compared to original_plus:

1. OLE drag/drop support
2. control characters (e.g., ctrl+C) map to current short cut (e.g., ctrl+c -> copy)
instead of changing drives
3. cut (ctrl+X) followed by paste (ctrl+V) translates into a file move as one would expect
4. left and right arrows in the tree view expand and collapse folders like in the Explorer
5. added context menus in both panes
6. improved the means by which icons are displayed for files
7. F12 runs notepad or notepad++ on the selected file
8. moved the ini file location to %AppData%\Roaming\Microsoft\WinFile
9. File.Search can include a date which limits the files returned to those after the date provided;
the output is also sorted by the date instead of by the name
10. File.Search includes an option as to whether to include sub-directories
11. ctrl+K starts a command shell (ConEmu if installed) in the current directory; shfit+ctrl+K
starts an elevated command shell (cmd.exe only)
12. File.Goto (ctrl+G) enables one to type a few words of a path and get a list of directories;
selecting one changes to that directory.  Only drive c: is indexed.
13. UI shows  reparse points (e.g., Junction points) as such
14. added simple forward / back navigation (probably needs to be improved)
15. View command has a new option to sort by date forward (oldest on top);
normal date sorting is newest on top

You can read the code for more details.

## Contributing

As mentioned above, this project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## License

Copyright (c) Microsoft Corporation. All rights reserved.

Licensed under the [MIT](LICENSE) License.