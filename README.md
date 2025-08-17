# SCSS Source Files for Radzen Blazor Components

Provides SCSS source files from **Radzen.Blazor** components for custom theme development.

[![License - MIT](https://img.shields.io/github/license/cytoph/blazor-radzen-theming?logo=github&style=for-the-badge)](https://github.com/cytoph/blazor-radzen-theming/blob/master/LICENSE)
[![NuGet Version](https://img.shields.io/nuget/v/Blazor.Radzen.Theming?logo=nuget&style=for-the-badge)](https://www.nuget.org/packages/Blazor.Radzen.Theming/)

## About

This package contains the complete collection of SCSS source files from the **Radzen.Blazor** components library, making them available for custom theme development. Instead of being limited to Radzen's pre-built themes, you can now access the original component stylesheets and create entirely custom themes tailored to your application's design requirements.

The package automatically includes the correct version of **Radzen.Blazor** as a dependency, ensuring that the SCSS files always match the component library version you're using. This eliminates version compatibility issues and provides a seamless theming experience.

## Usage

### Installation and File Location

Install the package via **NuGet Package Manager** or **.NET CLI**:

```bash
dotnet add package Blazor.Radzen.Theming
```

**Important:** You should not separately install **Radzen.Blazor**, as this package already includes it as a dependency. This ensures the SCSS files always match the component library version.

After installation and during project restore, the SCSS files are automatically placed in your project's `obj` directory under `Radzen.Blazor`. This happens through a build target in a .props file that runs during the restore process. The files are placed in the `obj` directory because it's typically included in `.gitignore`, preventing the theme source files from being accidentally committed to version control.

### Creating Custom Themes

1. **Copy a base theme:** Navigate to `obj/Radzen.Blazor/` in your project and copy one of the existing theme files (e.g., `standard.scss`, `material.scss`, etc.) to your own project directory (e.g., `wwwroot/`).

2. **Update import paths:** In your copied theme file, modify the `@import` statements to point to the SCSS files in the `obj` directory. For example, if your theme file is in `wwwroot/`, the imports should look like:
   ```scss
   @import '../obj/Radzen.Blazor/variables';
   @import '../obj/Radzen.Blazor/components';
   // ... other imports
   ```

3. **Customize your theme:** Modify SCSS variables, add your own styles, or override component styles as needed in your theme file.

4. **Compile SCSS to CSS:** Use a SCSS compiler to build your theme file into CSS. One option is [DartSassBuilder](https://github.com/someuser/DartSassBuilder), which can automatically compile SCSS files in your project during build. As of this writing, this is also a transient dependency of **Radzen.Blazor**, so it should already be available in your project.

5. **Include the compiled CSS:** Add the compiled CSS file to your application's HTML by adding it in the same file as the `RadzenTheme` component. For example, if your compiled CSS is `mytheme.css`, you can include it like this:
   ```html
   <component type="typeof(RadzenTheme)" render-mode="ServerPrerendered" param-Theme="@("standard")" />
   <link rel="stylesheet" href="~/css/mytheme.css" />
   ```
   
   Make sure to set the `Theme` parameter of the RadzenTheme component to the existing Radzen theme your custom theme is based upon.

   For more information on where to place these elements in your application, refer to the [Radzen Blazor Get Started guide](https://blazor.radzen.com/get-started).

## Disclaimer

This project is not affiliated with Radzen Ltd. in any way. It is an independent package created to provide easier access to **Radzen.Blazor**'s SCSS source files for custom theming purposes.

Special thanks to the Radzen team for creating and maintaining the excellent **Radzen.Blazor** component library. If you find their components useful, please consider supporting their work through their official channels and documentation at [radzen.com](https://www.radzen.com/).
