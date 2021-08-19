---
title: "Splash screens"
description: ".NET Multi-platform App UI (.NET MAUI) splash screens can be displayed when an app is launched, while the app's initialization process completes."
ms.date: 06/07/2021
---

# Splash screens

<!-- Todo: Move this content into the images doc, once it migrates over? -->

.NET Multi-platform App UI (.NET MAUI) apps can display a splash screen while their initialization process completes. The splash screen is displayed immediately when an app is launched, providing immediate feedback to users while app resources are initialized. Once the app is ready for interaction, the splash screen is dismissed.

Splash screens are a composite of an image and a background color, which can both be customized. The standard platform image formats are supported, including Scalable Vector Graphics (SVG) files.

> [!TIP]
> The SVG format is the recommended file format for .NET MAUI splash screens.

.NET MAUI splash screens are specified by dragging an image into the **Resources** folder of your single project, and setting the build action of the image to **MauiSplashScreen** in the **Properties** window. This creates a corresponding entry in your single project .csproj file:

```
<MauiSplashScreen Include="Resources\Images\splashscreen.svg" />
```

> [!WARNING]
> Splash screen files names must be lowercase, start and end with a letter character, and contain only alphanumeric characters or underscores.

As well as specifying an image for your app's splash screen you can also specify a background color:

```
<MauiSplashScreen Include="Resources\Images\splashscreen.svg" Color="#512BD4" />
```

<!-- Todo: Valid color values are actually derived from the SKColor struct, rather than Microsoft.Maui.Graphics.Colors -->
Color values can be specified in hexadecimal, or as a .NET MAUI color. For example, `Color="Red"` is valid.

At build time, .NET MAUI takes the splash screen and resizes it to the correct size for your target platform and device. The splash screen is then added to your app package.

<!-- markdownlint-disable MD025 -->

# [Android](#tab/android)

On Android, the splash screen is added to your app package as **Resourcs/values/maui_colors.xml** and **Resources/drawable/maui_splash_image.xml**. .NET MAUI apps use the `Maui.SplashTheme` by default, which ensures that a splash screen will be displayed if present. Therefore, you should omit any themes from your manifest file.

# [iOS](#tab/ios)

On iOS, the splash screen is added to the app package as a storyboard named `MauiSplash.storyboard`, which is set as the app's `UILaunchStoryboardName`. Therefore, your app should not set a `LaunchScreen.storyboard`, and you should not set `UILaunchStoryboardName` in your **Info.plist** file.

# [Windows](#tab/windows)

On Windows, the splash screen is inserted into the app package as an assets file.

---

> [!TIP]
> Effective splash screens are often simple, being compromised of a simple centered image and a background color that looks good regardless of the platform your app is running on.

For more advanced splash screen scenarios, native splash screen approaches still apply.