# index.js

This is a documentation file for the `index.js` script.

## Description

The `index.js` script defines a router for handling requests related to tasks and pending images. It uses the Express framework and interacts with the `../core/tasks` module to retrieve tasks and pending images.

## Usage

To use the `index.js` script, require it in your Node.js application:

```javascript
const express = require("express");
const router = express.Router();
const {
  getTasks,
  getPendingUpscales,
  getPendingImages,
} = require("../core/tasks");

// Define routes and handlers using the router

module.exports = router;
```

### Routes

- `/`: Handles the root route and renders the `index` view. It retrieves tasks, pending images, and pending upscales using the `getTasks`, `getPendingImages`, and `getPendingUpscales` functions respectively. The retrieved data is then passed to the `index` view for rendering.
