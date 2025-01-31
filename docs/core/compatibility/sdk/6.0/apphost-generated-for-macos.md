---
title: "Breaking change: Generate apphost for macOS"
description: Learn about the breaking change in .NET 6 where an executable is generated by default when building on macOS.
ms.date: 07/13/2021
---
# Generate apphost for macOS

When building on macOS, the .NET SDK now [produces an executable](../../../deploying/index.md#produce-an-executable) for app projects.

Since .NET Core 3.0, the .NET SDK has created an executable for app projects when building on non-macOS operating systems. However, it did not create an executable on macOS since we weren't signing this binary. That resulted in an app that was recognized as dangerous by the OS, which made it hard for the user to run it. The .NET 6 SDK can sign the app executable, so it now produces the executable by default.

## Version introduced

.NET SDK 6.0.100

## Old behavior

The apphost executable was not generated by default. You could explicitly ask the SDK to generate an executable by setting the `UseAppHost` property to `true`.

## New behavior

The apphost is now generated by default and is signed using the native command-line codesign, making it easier for users to execute the binary.

## Reason for change

We implemented the necessary changes in the HostModel to be able to code-sign executables.

## Recommended action

If your app targets macOS and you don't want the apphost to be generated, set the `UseAppHost` property to `false` to prevent the SDK from generating this file.

## Affected APIs

N/A

<!--

### Affected APIs

Not detectable via API analysis.

-->
