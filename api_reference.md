---
title: Mermaid API Reference
description: Comprehensive API reference for Mermaid, including all public methods, their parameters, return values, and usage examples.
---

# Mermaid API Reference

This document provides a comprehensive reference for the Mermaid API, including all public methods, their parameters, return values, and usage examples.

## Table of Contents

1. [Initialization](#initialization)
2. [Rendering](#rendering)
3. [Parsing](#parsing)
4. [Configuration](#configuration)
5. [Utility Functions](#utility-functions)

## Initialization

### initialize(userOptions)

Initializes Mermaid with the given options.

**Parameters:**
- `userOptions` (optional): An object containing initial Mermaid configuration options.

**Usage:**
```javascript
mermaid.initialize({
  theme: 'forest',
  logLevel: 'error',
  securityLevel: 'strict',
  startOnLoad: true
});
```

## Rendering

### render(id, text, svgContainingElement)

Renders a diagram from the given text.

**Parameters:**
- `id` (string): The ID to use for the rendered SVG.
- `text` (string): The Mermaid diagram definition.
- `svgContainingElement` (optional, Element): The element to render the SVG into.

**Returns:** A Promise that resolves to an object containing:
- `diagramType` (string): The type of the rendered diagram.
- `svg` (string): The rendered SVG code.
- `bindFunctions` (function): Diagram-specific binding functions.

**Usage:**
```javascript
const element = document.getElementById('mermaid');
mermaid.render('mermaid-1', 'graph TD; A-->B;', element)
  .then(result => {
    console.log(result.svg);
  });
```

## Parsing

### parse(text, parseOptions)

Parses and validates the syntax of a Mermaid diagram definition.

**Parameters:**
- `text` (string): The Mermaid diagram definition.
- `parseOptions` (optional, object): Options for parsing.
  - `suppressErrors` (boolean): If true, returns false instead of throwing an error for invalid diagrams.

**Returns:** A Promise that resolves to an object containing:
- `diagramType` (string): The type of the parsed diagram.
- `config` (object): The parsed configuration.

**Usage:**
```javascript
mermaid.parse('graph TD; A-->B;')
  .then(result => {
    console.log(result.diagramType);
  });
```

## Configuration

### getConfig()

Retrieves the current Mermaid configuration.

**Returns:** The current configuration object.

**Usage:**
```javascript
const config = mermaid.getConfig();
console.log(config);
```

### setConfig(config)

Sets the Mermaid configuration.

**Parameters:**
- `config` (object): The configuration object to set.

**Usage:**
```javascript
mermaid.setConfig({
  theme: 'dark',
  logLevel: 'info'
});
```

### updateSiteConfig(config)

Updates the site-wide Mermaid configuration.

**Parameters:**
- `config` (object): The configuration object to update.

**Usage:**
```javascript
mermaid.updateSiteConfig({
  startOnLoad: false
});
```

## Utility Functions

### getDiagramFromText(text, metadata)

Creates a Diagram object from the given text.

**Parameters:**
- `text` (string): The Mermaid diagram definition.
- `metadata` (optional, object): Additional metadata for the diagram.
  - `title` (string): The title of the diagram.

**Returns:** A Promise that resolves to a Diagram object.

**Usage:**
```javascript
mermaid.getDiagramFromText('graph TD; A-->B;', { title: 'Simple Flowchart' })
  .then(diagram => {
    console.log(diagram.type);
  });
```

### reset()

Resets the Mermaid configuration to the default settings.

**Usage:**
```javascript
mermaid.reset();
```

### globalReset()

Resets the Mermaid configuration to the original default settings.

**Usage:**
```javascript
mermaid.globalReset();
```

This API reference provides an overview of the main functions available in the Mermaid library. For more detailed information on specific diagram types and advanced usage, please refer to the relevant sections in the documentation.