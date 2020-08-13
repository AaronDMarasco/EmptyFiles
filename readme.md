<!--
GENERATED FILE - DO NOT EDIT
This file was generated by [MarkdownSnippets](https://github.com/SimonCropp/MarkdownSnippets).
Source File: /readme.source.md
To change this file edit the source file and then run MarkdownSnippets.
-->

# <img src="/src/icon.png" height="30px"> EmptyFiles

[![Build status](https://ci.appveyor.com/api/projects/status/4mrhpal9rwtqajws/branch/master?svg=true)](https://ci.appveyor.com/project/SimonCropp/EmptyFiles)
[![NuGet Status](https://img.shields.io/nuget/v/EmptyFiles.svg?label=EmptyFiles)](https://www.nuget.org/packages/EmptyFiles/)

A collection of minimal binary files.

Support is available via a [Tidelift Subscription](https://tidelift.com/subscription/pkg/nuget-emptyfiles?utm_source=nuget-emptyfiles&utm_medium=referral&utm_campaign=enterprise).

<!-- toc -->
## Contents

  * [Files](#files)
    * [Document](#document)
    * [Image](#image)
    * [Sheet](#sheet)
    * [Slide](#slide)
  * [Usage](#usage)
    * [CreateFile](#createfile)
    * [GetPathFor](#getpathfor)
    * [IsEmptyFile](#isemptyfile)
    * [AllPaths](#allpaths)
    * [UseFile](#usefile)
    * [Extensions helper](#extensions-helper)
  * [Security contact information](#security-contact-information)<!-- endtoc -->


## NuGet package

 * https://nuget.org/packages/EmptyFiles/


## Files

All files: https://github.com/SimonCropp/EmptyFiles/tree/master/files

### Archive <!-- include: extensions. path: /src/EmptyFiles.Tests/extensions.include.md -->

  * 7z (32 bytes)
  * bz2 (14 bytes)
  * gz (29 bytes)
  * tar (1.5 KB)
  * zip (22 bytes)
### Document

  * docx (1.9 KB)
  * odt (2.2 KB)
  * pdf (291 bytes)
  * rtf (6 bytes)
### Image

  * bmp (58 bytes)
  * dds (136 bytes)
  * dib (58 bytes)
  * emf (620 bytes)
  * exif (734 bytes)
  * gif (799 bytes)
  * heif (209 bytes)
  * ico (70 bytes)
  * j2c (270 bytes)
  * jfif (734 bytes)
  * jp2 (355 bytes)
  * jpc (270 bytes)
  * jpe (734 bytes)
  * jpeg (734 bytes)
  * jpg (734 bytes)
  * jxr (300 bytes)
  * pbm (10 bytes)
  * pcx (131 bytes)
  * pgm (12 bytes)
  * png (119 bytes)
  * ppm (14 bytes)
  * rle (58 bytes)
  * tga (543 bytes)
  * tif (250 bytes)
  * tiff (250 bytes)
  * wdp (300 bytes)
  * webp (228 bytes)
  * wmp (300 bytes)
### Sheet

  * ods (2.7 KB)
  * xlsx (4.5 KB)
### Slide

  * odp (7.8 KB)
  * pptx (13.3 KB) <!-- end include: extensions. path: /src/EmptyFiles.Tests/extensions.include.md -->


## Usage


### CreateFile

Creates a new empty file

<!-- snippet: CreateFile -->
<a id='snippet-createfile'></a>
```cs
AllFiles.CreateFile(pathOfFileToCreate);
```
<sup><a href='/src/EmptyFiles.Tests/Tests.cs#L46-L48' title='File snippet `createfile` was extracted from'>snippet source</a> | <a href='#snippet-createfile' title='Navigate to start of snippet `createfile`'>anchor</a></sup>
<!-- endsnippet -->

Throws an exception if the extension is not known. There is also a `TryCreateFile` that will return false if the extension is not known.

Use the optional `useEmptyStringForTextFiles` to create a empty text file if the extension is text. The file will be UTF8 no BOM as per https://www.unicode.org/versions/Unicode5.0.0/ch02.pdf "Use of a BOM is neither required nor recommended for UTF-8".


### GetPathFor

Gets the path to an empty file for a given extension

<!-- snippet: GetPathFor -->
<a id='snippet-getpathfor'></a>
```cs
var path = AllFiles.GetPathFor("jpg");
```
<sup><a href='/src/EmptyFiles.Tests/Tests.cs#L31-L33' title='File snippet `getpathfor` was extracted from'>snippet source</a> | <a href='#snippet-getpathfor' title='Navigate to start of snippet `getpathfor`'>anchor</a></sup>
<!-- endsnippet -->

Throws an exception if the extension is not known. There is also a `TryGetPathFor` that will return false if the extension is not known.


### IsEmptyFile

Returns true if the target file is an empty file.

<!-- snippet: IsEmptyFile -->
<a id='snippet-isemptyfile'></a>
```cs
var path = AllFiles.GetPathFor("jpg");
Assert.True(AllFiles.IsEmptyFile(path));
var temp = Path.GetTempFileName();
Assert.False(AllFiles.IsEmptyFile(temp));
```
<sup><a href='/src/EmptyFiles.Tests/Tests.cs#L72-L77' title='File snippet `isemptyfile` was extracted from'>snippet source</a> | <a href='#snippet-isemptyfile' title='Navigate to start of snippet `isemptyfile`'>anchor</a></sup>
<!-- endsnippet -->


### AllPaths

Enumerates all empty files

<!-- snippet: AllPaths -->
<a id='snippet-allpaths'></a>
```cs
foreach (var path in AllFiles.AllPaths)
{
    Trace.WriteLine(path);
}
```
<sup><a href='/src/EmptyFiles.Tests/Tests.cs#L97-L102' title='File snippet `allpaths` was extracted from'>snippet source</a> | <a href='#snippet-allpaths' title='Navigate to start of snippet `allpaths`'>anchor</a></sup>
<!-- endsnippet -->


### UseFile

Use or replace a file

<!-- snippet: UseFile -->
<a id='snippet-usefile'></a>
```cs
AllFiles.UseFile(Category.Document, pathToFile);
Assert.Contains(pathToFile, AllFiles.DocumentPaths);
```
<sup><a href='/src/EmptyFiles.Tests/Tests.cs#L109-L112' title='File snippet `usefile` was extracted from'>snippet source</a> | <a href='#snippet-usefile' title='Navigate to start of snippet `usefile`'>anchor</a></sup>
<!-- endsnippet -->


### Extensions helper


#### IsText

https://github.com/sindresorhus/text-extensions/blob/master/text-extensions.json

<!-- snippet: IsText -->
<a id='snippet-istext'></a>
```cs
Assert.True(Extensions.IsText("file.txt"));
Assert.False(Extensions.IsText("file.bin"));
Assert.True(Extensions.IsText(".txt"));
Assert.False(Extensions.IsText(".bin"));
Assert.True(Extensions.IsText("txt"));
Assert.False(Extensions.IsText("bin"));
```
<sup><a href='/src/EmptyFiles.Tests/ExtensionsTests.cs#L11-L18' title='File snippet `istext` was extracted from'>snippet source</a> | <a href='#snippet-istext' title='Navigate to start of snippet `istext`'>anchor</a></sup>
<!-- endsnippet -->


#### AddTextExtension

<!-- snippet: AddTextExtension -->
<a id='snippet-addtextextension'></a>
```cs
Extensions.AddTextExtension("ext1");
Extensions.AddTextExtension(".ext2");
Assert.True(Extensions.IsText("ext1"));
Assert.True(Extensions.IsText("ext2"));
```
<sup><a href='/src/EmptyFiles.Tests/ExtensionsTests.cs#L24-L29' title='File snippet `addtextextension` was extracted from'>snippet source</a> | <a href='#snippet-addtextextension' title='Navigate to start of snippet `addtextextension`'>anchor</a></sup>
<!-- endsnippet -->


#### RemoveTextExtension

<!-- snippet: RemoveTextExtension -->
<a id='snippet-removetextextension'></a>
```cs
Extensions.AddTextExtension("ext1");
Extensions.AddTextExtension(".ext2");
Assert.True(Extensions.IsText("ext1"));
Assert.True(Extensions.IsText("ext2"));
Extensions.RemoveTextExtension("ext1");
Extensions.RemoveTextExtension(".ext2");
Assert.False(Extensions.IsText("ext1"));
Assert.False(Extensions.IsText("ext2"));
```
<sup><a href='/src/EmptyFiles.Tests/ExtensionsTests.cs#L35-L44' title='File snippet `removetextextension` was extracted from'>snippet source</a> | <a href='#snippet-removetextextension' title='Navigate to start of snippet `removetextextension`'>anchor</a></sup>
<!-- endsnippet -->


## Security contact information

To report a security vulnerability, use the [Tidelift security contact](https://tidelift.com/security). Tidelift will coordinate the fix and disclosure.


## Icon

[Hollow](https://thenounproject.com/term/hollow/51835/) designed by [Michael Senkow](https://thenounproject.com/mhsenkow/) from [The Noun Project](https://thenounproject.com).
