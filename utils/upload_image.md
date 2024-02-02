## Functions in upload_image.js

This documentation provides an overview of the functions available in the `upload_image.js` script.

### `findFile(fileName)`

This asynchronous function takes in a `fileName` parameter and searches for a file with the given name in the Google Drive folder specified by `DRIVE_FOLDER_ID`. It returns the ID of the file if found, otherwise it returns `null`.

Example usage:

```javascript
const fileId = await findFile("example.png");
```

### `upload(imageName, imageUrl, withFormat = true)`

This asynchronous function is used to upload an image to Google Drive. It takes in three parameters:

- `imageName`: The name of the image file.
- `imageUrl`: The URL of the image to be uploaded.
- `withFormat` (optional): A boolean flag indicating whether to append the file extension ".png" to the `imageName`. By default, it is set to `true`.

Example usage:

```javascript
const imageLink = await upload("example", "https://example.com/image.png");
```

The function retrieves the image data from the provided `imageUrl` using Axios and creates a media object with the image data and MIME type "image/png". It then checks if a file with the same `imageName` already exists in the Google Drive folder. If it exists, the function updates the file with the new media data. If it doesn't exist, the function creates a new file with the specified name and uploads the media data.

The function returns the URL of the uploaded file in Google Drive.
