# Troubleshooting

This guide addresses common issues you might encounter when using Mermaid, including rendering problems, configuration errors, and integration challenges. If you're experiencing difficulties, follow the steps below to diagnose and resolve the problem.

## Rendering Issues

### Diagram Not Displaying

If your diagram is not displaying at all, try the following:

1. Check your syntax: Ensure that your Mermaid syntax is correct. Even small errors can prevent the diagram from rendering.

2. Verify Mermaid initialization: Make sure Mermaid is properly initialized on your page. Add the following code before your diagram:

   ```javascript
   <script>
   mermaid.initialize({ startOnLoad: true });
   </script>
   ```

3. Check browser console: Open your browser's developer tools and look for any error messages in the console that might provide more information about the issue.

### Incorrect Diagram Layout

If your diagram is rendering but doesn't look as expected:

1. Review diagram type: Ensure you're using the correct diagram type for your needs (e.g., flowchart, sequence diagram, gantt chart).

2. Check direction: For flowcharts, verify that you've specified the correct direction (TB, BT, RL, or LR).

3. Validate syntax: Double-check your syntax, paying special attention to node connections and styling.

## Configuration Errors

### Theme Issues

If you're experiencing problems with diagram appearance:

1. Verify theme configuration: Check that your theme is properly set in the Mermaid configuration:

   ```javascript
   mermaid.initialize({
     theme: 'default' // or 'forest', 'dark', 'neutral'
   });
   ```

2. Custom themes: If using a custom theme, ensure all required variables are defined in your `themeVariables` object.

### Security Levels

If you're unable to use certain features due to security restrictions:

1. Check security level: Verify your current security level setting:

   ```javascript
   mermaid.initialize({
     securityLevel: 'strict' // or 'loose', 'sandbox'
   });
   ```

2. Adjust as needed: If you need to use features blocked by the `strict` level, consider changing to `loose`, but be aware of potential security implications.

## Integration Challenges

### Issues with Specific Frameworks

#### React

1. Use a wrapper component: Consider using a wrapper component to handle Mermaid rendering, like `mermaid-react`.

2. Manual rendering: If not using a wrapper, ensure you're calling `mermaid.contentLoaded()` after your component mounts.

#### Vue

1. Use a plugin: Consider using the `vue-mermaid-string` plugin for easier integration.

2. Custom directive: If not using a plugin, create a custom directive to handle Mermaid rendering.

### Server-Side Rendering (SSR)

If you're using SSR and encountering issues:

1. Client-side only: Ensure Mermaid is only initialized and rendered on the client-side, as it requires a browser environment.

2. Use dynamic imports: Consider using dynamic imports to load Mermaid only in the browser:

   ```javascript
   if (typeof window !== 'undefined') {
     import('mermaid').then((mermaid) => {
       mermaid.initialize({ startOnLoad: true });
     });
   }
   ```

## Performance Issues

If you're experiencing slow rendering or browser performance problems:

1. Limit diagram complexity: Very large or complex diagrams can slow down rendering. Consider breaking them into smaller, more manageable parts.

2. Check for loops: Ensure your diagrams don't contain any unintended loops, which can cause performance issues.

3. Use `maxTextSize`: If dealing with large diagrams, set the `maxTextSize` configuration option to limit the size of diagrams:

   ```javascript
   mermaid.initialize({
     maxTextSize: 50000 // Adjust as needed
   });
   ```

## Still Having Issues?

If you've tried these troubleshooting steps and are still experiencing problems:

1. Check the [Mermaid documentation](https://mermaid-js.github.io/mermaid/) for any updates or known issues.

2. Search the [GitHub issues](https://github.com/mermaid-js/mermaid/issues) to see if others have encountered similar problems.

3. If your issue seems unique, consider opening a new issue on GitHub with a detailed description of the problem, including your Mermaid version, browser, and a minimal reproducible example.

Remember to always use the latest version of Mermaid when possible, as many issues are resolved in newer releases.