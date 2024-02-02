# process_google.js

This script provides functions for interacting with a Google Spreadsheet using the `google-spreadsheet` library.

1. Call the functions as needed.

## Functions

### getRows

```javascript
async function getRows(doc_id) {
  // ...
}
```

This function retrieves rows from a Google Spreadsheet based on the provided document ID.

- `doc_id`: The ID of the Google Spreadsheet.

Returns an array of rows, where each row is an object with the following properties:

- `id`: The ID of the row.
- `command`: The command value from the row.
- `tag`: The tag value from the row.

### setTaskAsDone

```javascript
async function setTaskAsDone(url, imagedata, changeStatus = true) {
  // ...
}
```

This function sets a task as done in the Google Spreadsheet based on the provided parameters.

- `url`: The URL of the image.
- `imagedata`: An object containing image data, including the `commandId` and `messageId`.
- `changeStatus` (optional): A boolean indicating whether to change the status. Default is `true`.

Returns an array of rows.

### getRowIdBaseOnMessageId

```javascript
async function getRowIdBaseOnMessageId(messageId, url) {
  // ...
}
```

This function retrieves the row ID based on the provided message ID from the Google Spreadsheet.

- `messageId`: The message ID.
- `url`: The URL of the image.

Returns the ID of the row if found, otherwise `null`.
