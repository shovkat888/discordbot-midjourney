1. The script requires several modules and files using the `require` function. These modules and files include:

   - The `uuid` module from the "uuid" package.
   - The `botSelectedImage`, `botFullFlow`, `botSelectImage`, `botDownloadImage`, `botFetchMessages`, `botFetchMessage`, `botGetChildUrl`, `botGetParent`, and `botSendRelax` functions from the "../bot" file.
   - The `getTask`, `getTasks`, `getImageQueue`, `createImageQueue`, `createTask`, `deleteTask`, `getPendingImages`, `updateCommand`, `getPendingUpscales`, and `updateTask` functions from the "../core/tasks" file.
   - The `TASK_TYPES` constant from the "../utils/constants" file.
   - The `getRows` and `getRowIdBaseOnMessageId` functions from the "../utils/process_google" file.
   - The `upload` function from the "../utils/upload_image" file.

2. The script defines two controllers: `createTasksController` and `selectImageController`.

   - The `createTasksController` is an asynchronous function that handles the creation of tasks. It takes a request (`req`) and a response (`res`) as parameters.
   - Inside the `createTasksController`, it retrieves the `link_id`, `link_id_auto`, and `type` from the request body.
   - It then calls the `getRows` function with the `link` to retrieve the document rows asynchronously.
   - After that, it creates a new task object with a unique ID generated using the `uuid` module and an empty array of commands.
   - It iterates over the `docRows` and populates the `commands` array with objects containing the `command` and a unique ID generated using the task ID and element ID.
   - Finally, it calls the `createTask` function with the new task object and redirects the response to the root ("/") route.

3. The `selectImageController` is an asynchronous function that handles the selection of images for a specific command. It takes a request (`req`) and a response (`res`) as parameters.

   - It retrieves the `commandId` and `selectedImage` from the query parameters of the request.
   - It then calls the `getImageQueue` function to get the current image queue asynchronously.
   - If there is no existing image queue, it creates a new task object with an empty array of images and adds the `commandId` and `selectedImage` to the array. Then it calls the `createImageQueue` function with the new task object.
   - If there is an existing image queue, it searches for an image with a matching `commandId`. If found, it updates the image with the selected image. Otherwise, it adds a new image object to the image queue with the `commandId` and `selectedImage`.
   - Finally, it calls the `createImageQueue` function with the updated or new image queue and sends a success status (200) in the response.
     Here is the documentation for each function in the provided script:

4. `UploadSelectedImages`: This function is an asynchronous controller that handles the upload of selected images. It retrieves the task ID from the query parameters and calls the `getImageQueue` and `getPendingImages` functions to retrieve the image queue and pending images, respectively. It then iterates over the images in the queue and checks if there is a corresponding pending image for each command. If a pending image is found, it calls the `botDownloadImage` function to download the selected image, updates the command with the downloaded image URL using the `updateCommand` function, and checks if all commands in the task have been processed. If all commands have been processed, it deletes the task and the image queue. Finally, it renders a "success" view. If any error occurs during the process, it renders an "error" view with the error message.

5. `runTask`: This function is an asynchronous controller that runs a task. It retrieves the task ID, time, incomplete_only, and auto_incomplete from the request body. It first calls the `botSendRelax` function to send a relaxation message. Then, depending on the task type, it calls the `botFullFlow` or `botSelectedImage` function multiple times. The number of times it executes the task depends on the `auto_incomplete` flag. If `auto_incomplete` is true, it executes the task three times, otherwise it executes it once. The `botFullFlow` and `botSelectedImage` functions handle the execution of different types of tasks. Finally, it renders a "success" view. If any error occurs during the process, it renders an "error" view with the error message.

6. `upscaleImageController`: This function is an asynchronous controller that handles the upscaling of images. It calls the `getPendingUpscales` function to retrieve a list of pending images. It then iterates over the images and calls the `botDownloadImage` function to download each image. Finally, it renders a "success" view. If any error occurs during the process, it renders an "error" view with the error message.

7. `deleteTaskController`: This function is an asynchronous controller that deletes a task. It retrieves the task ID from the query parameters and calls the `deleteTask` function to delete the task. Finally, it redirects the user to the homepage ("/"). If any error occurs during the process, it renders an "error" view with the error message.

8. `editTaskController`: This function is an asynchronous controller that edits a task. It retrieves the task ID, type, and commands from the request body. It calls the `getTask` function to retrieve the current task. It then iterates over the commands and updates the command's content based on the provided commands. Finally, it calls the `updateTask` function to update the task with the new type and commands. Finally, it redirects the user to the homepage ("/"). If any error occurs during the process, it logs the error and sends a 500 status with an error message.

9. `checkVersion`: This function is an asynchronous controller that checks the version of messages and uploads images. It retrieves the number of messages and message ID from the request body. It calls the `botFetchMessages` function to fetch the specified number of messages. It then checks if a specific message ID is provided and fetches the message and its parent using the `botFetchMessage` and `botGetParent` functions, respectively. If a parent exists, it adds the message and parent to an images array. After that, it iterates over the fetched messages and their parents, and for each pair, it retrieves the URL of the child message using the `botGetChildUrl` function. It then calls the `getRowIdBaseOnMessageId` function to get the image ID based on the parent message ID and URL. If an image ID is found, it calls the `upload` function to upload the image. Finally, it renders a "success" view. If any error occurs during the process, it renders an "error" view with the error message.
