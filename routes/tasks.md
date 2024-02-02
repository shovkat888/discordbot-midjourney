# tasks.js

This is a documentation file for the `tasks.js` script.

## Description

The `tasks.js` script defines routes and controllers for handling tasks and images related to tasks. It uses the Express framework and interacts with the `../core/tasks` module and `../controllers/tasks` module to perform various operations.

## Usage

To use the `tasks.js` script, require it in your Node.js application:

```javascript
const express = require("express");
const { getTask, getPendingImages } = require("../core/tasks");
const router = express.Router();
const {
  createTasksController,
  deleteTaskController,
  editTaskController,
  runTask,
  selectImageController,
  upscaleImageController,
  UploadSelectedImages,
  checkVersion,
} = require("../controllers/tasks");

// Define routes and handlers using the router

module.exports = router;
```

### Routes and Controllers

- `/task/create`: Handles the route for creating a new task. It uses the `createTasksController` controller to handle the request.

- `/task/delete`: Handles the route for deleting a task. It uses the `deleteTaskController` controller to handle the request.

- `/task/open`: Handles the route for opening a task for editing. It retrieves the task using the `getTask` function and renders the `edit` view with the task data.

- `/task/edit`: Handles the route for editing a task. It uses the `editTaskController` controller to handle the request.

- `/task/run`: Handles the route for running a task. It uses the `runTask` controller to handle the request.

- `/task/check-version`: Handles the route for checking the version of a task. It uses the `checkVersion` controller to handle the request.

- `/task/image/upscale`: Handles the route for upscaling an image related to a task. It uses the `upscaleImageController` controller to handle the request.

- `/task/images/review`: Handles the route for reviewing images related to a task. It retrieves the pending images using the `getPendingImages` function and renders the `select_image` view with the images and task ID.

- `/task/image/select`: Handles the route for selecting an image related to a task. It uses the `selectImageController` controller to handle the request.

- `/task/image/send`: Handles the route for sending selected images related to a task. It uses the `UploadSelectedImages` controller to handle the request.
