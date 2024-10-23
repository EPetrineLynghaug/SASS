# Lecture Notes, SASS Overview

SASS stands for **Syntactically Awesome Stylesheet**. It simplifies writing CSS by using a preprocessor to compile SASS or SCSS into regular CSS. Although browsers cannot understand SASS directly, tools like CodePen automatically compile SASS code. It's recommended to include SASS as a development dependency.

## Installation
<details>
  <summary><strong>Click to read more</strong></summary>


You can install SASS using different methods:

- **macOS and Windows (NPM)**: `npm install -g sass`
- **Windows (Chocolatey)**: `choco install sass`
- **macOS (Homebrew)**: `brew install sass/sass/sass`
</details>

## Key Features of SASS
<details>
  <summary><strong>Click to read more</strong></summary>

### Built-In Functionalities

SASS comes with built-in capabilities that help write more maintainable and robust CSS:

- **Nesting**: Mimics HTML structure, allowing for a more readable style hierarchy.
- **Mixins**: Enables reusable chunks of code.
- **Inheritance**: Allows properties from one selector to be extended to another.
- **Variables**: Store reusable values like colors, fonts, and sizes.

### Compilation and File Watching

To compile SASS:

- Basic compilation: `sass input.scss output.css`
- Automatically watch for changes: `sass --watch input.scss output.css`

Errors will be displayed in both the console and at the top of the file.

### Working with Folders

When working on larger projects, it's common to compile multiple files into a single output CSS file or handle entire folders.

### Partial Files

- SASS files that start with an underscore (`_`) are treated as partials and not compiled directly.
- Partials can be imported into other SASS files using the `@use` directive.

## Comments

- `/* */` for comments that should appear in the compiled CSS.
- `//` for comments that will not be included in the output.

## SASS Basics

### Variables

SASS variables start with `$` and can be used throughout the styles:

```scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```
### Nesting

SASS supports nested rules to reflect HTML structure:

```scss
nav {
  ul {
    li {
      a {
        color: $primary-color;
      }
    }
  }
}
```
### importing and Using Partials

Use the @use directive for partials to organize code into modules:
```scss
// _base.scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}

// styles.scss
@use 'base';

.inverse {
  background-color: base.$primary-color;
  color: white;
}
```


### Mixins

Mixins allow for reusable blocks of code:
```scss
@mixin theme($theme: DarkGray) {
  background: $theme;
  box-shadow: 0 0 1px rgba($theme, .25);
  color: #fff;
}

.info {
  @include theme;
}

.alert {
  @include theme($theme: DarkRed);
}
```

### Extending Selectors

Extend allows for sharing styles between selectors:
```scss

.button {
  padding: 10px 20px;
  border-radius: 5px;
}

.primary-button {
  @extend .button;
  background-color: $primary-color;
}
```

### Operators

SASS supports basic mathematical operators (+, -, *, /) and functions like math.div() to perform calculations.
</details>

## Work Along
<details>
  <summary><strong>Click to read more</strong></summary>

To demonstrate the concepts covered, follow these steps to create a mini project using SCSS:

1.	**Create an HTML File**
Start with a simple HTML file for the project.
2.	**Set Up main.scss**
Use main.scss as the main entry point for SASS compilation. This file will bundle all required mixins and styles.
3.	**Define Variables in SCSS**
Create variables for colors, spacing, and fonts. This makes it easier to update values and override settings, such as those from frameworks like Bootstrap.
4.	**Create Mixins**
Add mixins for flexible values, maps for color variables, and button hover effects. For example, to darken a button on hover, use the adjust function with lightness set to -10%.
5.	**Write a Function**
Functions in SASS are similar to mixins but typically perform calculations and return values. For example, use the Channel color method to adjust brightness based on background color for dark mode compatibility.
6.	**Organize Partials and Nesting**
Create partials for different sections (e.g., _headers.scss) and use nesting to reflect the structure of the HTML elements. Import variables, functions, and mixins at the top of each partial.
7.	**Style the Main Content**
In the content area, add styling for buttons using mixins and other standard elements. Be cautious with file names to avoid confusion during imports.
8.	**Add a Footer**
Style the footer based on the background color, automatically adjusting the text color for readability.

**Compiling and Testing**

Compile the SASS files and verify that the output works as expected.

**Additional Tips**

•	Partials are SCSS files starting with _ and included using @use.
•	To access variables from partials, use a namespace (e.g., base.$primary-color).
•	Do not modify the .css.map file, as it is used for source mapping. You can add it to .gitignore if needed.

### Setting Up the Development Environment

1.	**Install SASS as a Dev Dependency**

    ```bash 
    npm install -D sass
    ```
2.	**Add Scripts to package.json**
```json
"scripts": {
  "build": "sass scss/main.scss:css/main.css",
  "watch": "sass --watch scss/main.scss:css/main.css & live-server"
}
```
Note: The & operator works on UNIX systems (macOS/Linux). For Windows, install npm-run-all.

4.	**Cross-Platform Script Setup**
Use npm-run-all to make the project compatible across different operating systems:

```bash
npm install -D npm-run-all

```

**Update the package.json scripts:**
```json
"scripts": {
  "build": "sass scss/main.scss:css/main.css",
  "watch": "sass --watch scss/main.scss:css/main.css",
  "start": "live-server",
  "dev": "npm-run-all --parallel watch start"
}
```
**This configuration ensures the project runs seamlessly on all systems.**

This section provides step-by-step instructions for the mini-project setup, including the development environment configuration.
</details>