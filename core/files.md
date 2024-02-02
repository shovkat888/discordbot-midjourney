# files.js

This is a documentation file for the `files.js` script.

## Description

The `files.js` script provides functions for managing tasks and files.

## Usage

To use the `files.js` script, require it in your Node.js application:

```javascript
const files = require("./files.js");
```

### Functions

- `createTask(task)`: Adds a new task to the tasks list.
- `addPendingImage(image)`: Adds a new pending image to the pending images list.

### Variables

- `tasks`: An array containing the tasks loaded from the `tasks.json` file.
- `pendingUpscales`: An array containing the pending upscales loaded from the `pending_upscales.json` file.

Please note that the `pendingImages` variable is currently commented out in the script.
