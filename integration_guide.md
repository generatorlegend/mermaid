---
title: Mermaid Integration Guide
description: Learn how to integrate Mermaid into various environments, including web applications, documentation tools, and content management systems.
---

# Mermaid Integration Guide

This guide provides instructions on how to integrate Mermaid into various environments, such as web applications, documentation tools, and content management systems.

## Table of Contents

1. [Basic Web Integration](#basic-web-integration)
2. [Advanced Configuration](#advanced-configuration)
3. [Integration with Documentation Tools](#integration-with-documentation-tools)
4. [Integration with Content Management Systems](#integration-with-content-management-systems)
5. [Troubleshooting](#troubleshooting)

## Basic Web Integration

To integrate Mermaid into a web application, follow these steps:

1. Include the Mermaid library in your HTML file:

```html
<script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>
```

2. Initialize Mermaid:

```html
<script>
  mermaid.initialize({ startOnLoad: true });
</script>
```

3. Create a diagram using the Mermaid syntax within a `<div>` element with the `mermaid` class:

```html
<div class="mermaid">
  graph TD;
      A-->B;
      A-->C;
      B-->D;
      C-->D;
</div>
```

Mermaid will automatically render the diagram when the page loads.

## Advanced Configuration

For more control over the rendering process, you can use the `mermaid.run()` function:

```javascript
import mermaid from 'mermaid';

mermaid.initialize({ startOnLoad: false });

document.addEventListener('DOMContentLoaded', () => {
  mermaid.run({
    querySelector: '.mermaid',
    postRenderCallback: (id) => {
      console.log(`Diagram ${id} rendered successfully`);
    },
    suppressErrors: true
  });
});
```

This approach allows you to:
- Control when diagrams are rendered
- Specify a custom selector for diagram elements
- Add a callback function to be executed after each diagram is rendered
- Suppress errors if needed

## Integration with Documentation Tools

Many documentation tools support Mermaid out of the box or through plugins. Here are some popular options:

### Markdown-based Tools

1. **Docusaurus**: Supports Mermaid diagrams using the `mermaid` code block.
2. **VuePress**: Use the `vuepress-plugin-mermaidjs` plugin for Mermaid support.
3. **MkDocs**: Integrate Mermaid using the `mkdocs-mermaid2-plugin`.

### Other Documentation Tools

1. **Sphinx**: Use the `sphinxcontrib-mermaid` extension to add Mermaid support.
2. **AsciiDoc**: Some AsciiDoc processors support Mermaid diagrams natively or through extensions.

## Integration with Content Management Systems

For content management systems, you may need to:

1. Include the Mermaid library in your theme or template files.
2. Initialize Mermaid in your JavaScript code.
3. Ensure that your CMS allows the necessary HTML and JavaScript to be added to pages.

### WordPress Example

1. Enqueue the Mermaid script in your theme's `functions.php`:

```php
function enqueue_mermaid() {
    wp_enqueue_script('mermaid', 'https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js', array(), null, true);
}
add_action('wp_enqueue_scripts', 'enqueue_mermaid');
```

2. Initialize Mermaid in your theme's JavaScript file or in a custom script:

```javascript
document.addEventListener('DOMContentLoaded', () => {
  mermaid.initialize({ startOnLoad: true });
});
```

3. Use a shortcode or custom block to add Mermaid diagrams to your content.

## Troubleshooting

If you encounter issues with Mermaid integration:

1. Check the browser console for error messages.
2. Ensure that the Mermaid library is loaded correctly.
3. Verify that your diagram syntax is correct.
4. Use the `mermaid.parse()` function to validate your diagram syntax:

```javascript
try {
  const result = await mermaid.parse('graph TD; A-->B;');
  console.log('Diagram is valid:', result);
} catch (error) {
  console.error('Invalid diagram:', error);
}
```

5. If diagrams are not rendering, make sure they are within elements with the correct class (default is `mermaid`).

For more detailed information on Mermaid's API and configuration options, refer to the [Mermaid API Documentation](https://mermaid.js.org/config/setup/modules/mermaidAPI.html).