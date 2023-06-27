# maui-ios-system-font

In Xamarin.Forms it is possible to use platform-specific system fonts, such as `sans-serif-medium`  on Android and `.SFUI-Semibold` on iOS, without having to import them manually.

Now, using the `.SFUI-Semibold` font fails on iOS, it defaults to _Times New Roman_, which is the expected behavior for fonts that are unknown on iOS, AFAIK.

The code used for Xamarin.Forms and MAUI is the same and looks like this:

```xml
<Grid>
    <Label
        VerticalOptions="Center"
        HorizontalOptions="Center"
        VerticalTextAlignment="Center"
        HorizontalTextAlignment="Center"
        FontSize="Title"
        FontFamily="{OnPlatform iOS='.SFUI-Semibold'}"
        Text="This should be SFUI-Semibold!"/>
</Grid>
```

Side-by-side comparison of Xamarin.Forms (correct, left) and .NET MAUI (incorrect, right):

<div style="align: top">
    <img src="https://github.com/ewerspej/maui-ios-system-font/blob/main/Screenshots/SystemFontXF.PNG?raw=true" width="300" />
    <img src="https://github.com/ewerspej/maui-ios-system-font/blob/main/Screenshots/SystemFontMaui.PNG?raw=true" width="300" />
</div>

I've also tried removing the "." in front of the font name. When I do that, it doesn't default to Times New Roman, but instead a different font _(or font style)_ is used.
