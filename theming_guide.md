---
title: Mermaid Theming Guide
description: Learn how to customize the appearance of Mermaid diagrams using themes
---

# Mermaid Theming Guide

Mermaid allows you to customize the appearance of your diagrams using themes. This guide will walk you through the process of using built-in themes and creating custom themes for your Mermaid diagrams.

## Table of Contents

1. [Built-in Themes](#built-in-themes)
2. [Using Themes](#using-themes)
3. [Creating Custom Themes](#creating-custom-themes)
4. [Theme Variables](#theme-variables)
5. [Advanced Theming](#advanced-theming)

## Built-in Themes

Mermaid comes with several built-in themes that you can use out of the box. The available themes are:

- `default`
- `base`
- `dark`
- `forest`
- `neutral`

Each theme provides a unique look and feel for your diagrams.

## Using Themes

To use a built-in theme, you can specify it in your Mermaid configuration. Here's an example of how to set the theme:

```javascript
mermaid.initialize({
  theme: 'forest'
});
```

You can also set the theme using the `%%{init: { "theme": "forest" }}%%` directive at the beginning of your diagram code.

## Creating Custom Themes

To create a custom theme, you can extend an existing theme or create a new one from scratch. Here's how you can create a custom theme:

1. Define your theme variables
2. Create a theme object
3. Register your theme with Mermaid

Here's an example of creating a custom theme:

```javascript
import { getThemeVariables } from 'mermaid/dist/themes/theme-default';

const myCustomTheme = {
  ...getThemeVariables('default'),
  primaryColor: '#ff0000',
  primaryTextColor: '#00ff00',
  // Add more custom variables here
};

mermaid.initialize({
  theme: 'myCustomTheme',
  themeVariables: myCustomTheme
});
```

## Theme Variables

Theme variables allow you to customize various aspects of your diagrams. Some common theme variables include:

- `primaryColor`
- `primaryTextColor`
- `secondaryColor`
- `tertiaryColor`
- `fontFamily`

For a complete list of theme variables, refer to the theme files in the Mermaid source code.

## Advanced Theming

For more advanced theming options, you can create a custom theme function that returns theme variables based on user input. Here's an example:

```javascript
const getCustomTheme = (userPreferences) => {
  return {
    ...getThemeVariables('default'),
    primaryColor: userPreferences.primaryColor || '#ff0000',
    // Add more dynamic theming logic here
  };
};

mermaid.initialize({
  theme: 'customTheme',
  themeVariables: getCustomTheme(userPreferences)
});
```

This approach allows you to create dynamic themes that can be adjusted based on user preferences or other factors.

Remember to always sanitize user input and be cautious when applying custom themes to ensure the security and integrity of your Mermaid diagrams.

For more information on Mermaid configuration and advanced usage, refer to the Mermaid documentation and API reference.