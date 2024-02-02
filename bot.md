### Functions in bot.js

This documentation provides an overview of the functions available in the `bot.js` script.

#### `extractKey(extractor)`

This asynchronous function takes in an `extractor` parameter and iterates over it to extract the first key. It returns the extracted key.

Example usage:

```javascript
const key = await extractKey(someExtractor);
```

#### `waitForMessage(channel, time = 10, command = null)`

This asynchronous function waits for a message in a specified channel. It takes in three parameters:

- `channel`: The Discord channel to wait for the message in.
- `time` (optional): The time in minutes to wait for the message. By default, it is set to 10 minutes.
- `command` (optional): The command to filter the awaited message. If provided, the function will only consider messages that match the command.

Example usage:

```javascript
const message = await waitForMessage(someChannel, 5, "someCommand");
```

The function filters the awaited messages based on the provided command and checks if the message author is the bot specified by `BOT_ID`. It also handles embeds and performs additional checks on the message content. It returns the first matching message.

#### `getMessageButtons(message)`

This function takes in a `message` as a parameter and returns the buttons (components) present in the message.

Example usage:

```javascript
const buttons = getMessageButtons(someMessage);
```

#### `getUpscalingButtons(message)`

This function takes in a `message` as a parameter and returns the upscaling buttons (components) present in the message. It removes the last option, "Retry".

Example usage:

```javascript
const upscalingButtons = getUpscalingButtons(someMessage);
```

#### `botFullFlow(task, option, time, incomplete_only = true)`

This asynchronous function performs the full flow of the bot for a given task. It takes in four parameters:

- `task`: The task object containing commands to be executed.
- `option`: The option to be selected during the flow.
- `time`: The time in minutes to wait for each step of the flow.
- `incomplete_only` (optional): A boolean flag indicating whether to skip commands that are already marked as done. By default, it is set to `true`.

Example usage:

```javascript
await botFullFlow(someTask, "random", 10, false);
```

The function iterates over the commands in the task and performs various operations, such as sending a slash command, waiting for messages, clicking buttons, extracting attachment keys, uploading images, and updating command status. It handles different options based on the provided parameter.

#### `botSelectedImage(task, time, incomplete_only = true)`

This asynchronous function handles the flow of the bot for a selected image. It takes in three parameters:

- `task`: The task object containing commands to be executed.
- `time`: The time in minutes to wait for each step of the flow.
- `incomplete_only` (optional): A boolean flag indicating whether to skip commands that are already marked as done. By default, it is set to `true`.

Example usage:

```javascript
await botSelectedImage(someTask, 5, false);
```

The function performs similar operations to `botFullFlow` but focuses on handling the flow for a selected image.

#### `botDownloadImage(image, selectedOption, res)`

This asynchronous function handles the process of downloading an image from a message and performing an upscale operation. It takes in three parameters:

- `image`: The image object containing information about the image to be downloaded.
- `selectedOption`: The option selected for the upscale operation.
- `res`: The response object to send the downloaded image URL.

Example usage:

```javascript
const imageUrl = await botDownloadImage(someImage, "option", someResponse);
```

The function retrieves the image message from the specified channel and extracts the upscale options. It then clicks the specified option and waits for the prompt messages. The function extracts the attachment key from the last message, uploads the image to a storage service, and updates the command status. Finally, it returns the URL of the downloaded image.

#### `botFetchMessages(limit = 100)`

This asynchronous function fetches multiple messages from the specified channel. It takes in one optional parameter:

- `limit`: The maximum number of messages to fetch. By default, it is set to 100.

Example usage:

```javascript
const messages = await botFetchMessages(200);
```

The function fetches messages in chunks of 100 until the desired limit is reached. It returns a map of all the fetched messages.

#### `botFetchMessage(messageId)`

This asynchronous function fetches a specific message from the specified channel. It takes in one parameter:

- `messageId`: The ID of the message to fetch.

Example usage:

```javascript
const message = await botFetchMessage("123456789");
```

The function fetches the message with the provided ID from the channel and returns it.

#### `botGetParent(message)`

This asynchronous function retrieves the parent message of a given message. It takes in one parameter:

- `message`: The message object for which to find the parent.

Example usage:

```javascript
const parentMessage = await botGetParent(someMessage);
```

The function iteratively retrieves the parent message of the provided message until there is no more parent message. It returns the parent message.

#### `botGetChildUrl(message)`

This asynchronous function extracts the URL of the attachment from a given message. It takes in one parameter:

- `message`: The message object from which to extract the attachment URL.

Example usage:

```javascript
const attachmentUrl = await botGetChildUrl(someMessage);
```

The function extracts the attachment key from the provided message and returns the URL of the attachment.

#### `botSendRelax()`

This asynchronous function sends a "relax" message using a slash command. It does not take any parameters.

Example usage:

```javascript
await botSendRelax();
```

The function sends a "relax" message using the specified slash command.
