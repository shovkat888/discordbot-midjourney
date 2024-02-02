# tasks.js

This is a documentation file for the `tasks.js` script.

## Description

The `tasks.js` script provides functions for managing tasks and commands.

## Usage

To use the `tasks.js` script, require it in your Node.js application:

```javascript
const tasks = require("./tasks.js");
```

### Functions

- `getTasks()`: Retrieves all tasks.
- `getTask(taskId)`: Retrieves a specific task by ID.
- `createTask(newTask)`: Creates a new task.
- `getTasksWithPendingImages()`: Retrieves tasks with pending images.
- `deleteTask(taskId)`: Deletes a task by ID.
- `updateTask(taskId, data)`: Updates a task with new data.
- `getPendingImages()`: Retrieves pending images.
- `updateCommand(taskId, commandId, commandData)`: Updates a command within a task.
