# File Splitter and Merger
.NET Core 5 console tool which can:<br>
- split any binary file into any number of chunks
- split any binary file into chunks of any size in bytes
- merge any files
<br><br>

## Operation options:
-s = File split<br>
-m = File merge<br>
-i = Syntax info
<br><br>

## Split options:
-f = File path<br>
-d = Destination path<br>
-n = Split in number of chunks<br>
-s = Split in chunks of size in bytes
<br><br>

## Merge options:
-p = File parts<br>
-d = Destination file path
<br><br>

## Examples:
The first argument must be an operation option. The rest of the arguments can be in any order.<br>
### Split a file in chunks of specified size:
`FileSplitterMerger -s -f <path to file you want to split> -d <destination folder> -s <chunk size in bytes>`
<br><br>

### Split a file in number of chunks:
`FileSplitterMerger -s -f <path to file you want to split> -d <destination folder> -n <number of chunks>`
<br><br>

### Merge files:
`FileSplitterMerger -m -p <file path 1> <file path 2> <file path 3> -d <destination file path>`
<br><br>

## Publish
### Publish for Linux
The beauty of .NET 5 is it's multi-platform, so you can run this app on Linux by publishing it as follows:<br>
`dotnet publish -c release -r ubuntu.16.04-x64 --self-contained --output <destination folder>`
<br>

### Run on Linux:
`dotnet FileSplitterMerger.dll <arguments: see examples above for the arguments>`
<br><br>

### Publish for Windows
`dotnet publish -c release -r win-x64 --self-contained --output <destination folder>`
<br><br>

## Implementation notes
The files aren't loaded in memory but they're read and written using streams and buffers. This means that the memory fingerprint of this application is minimal and it can handle files of any size.<br>
The buffer size used by the streams adapts to the available machine memory for improved performance (e.g. with very large files)<br>
Custom enum description attributes are used for making argument detection and management easier.<br>
Dependency injection is used for the configuration.<br>Extensive unit tests have been included to ensure the correct behaviour in a variety of scenarios.
<br><br>

## Download
You can download this for Windows and Linux from the [releases section](https://github.com/erionpc/FileSplitterMerger/releases)
