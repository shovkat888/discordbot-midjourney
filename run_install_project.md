# Installation on docker

To install your project using the provided Dockerfile, follow these steps:

1. Make sure you have Docker installed on your system. You can download and install Docker from the official website: [Docker](https://www.docker.com/products/docker-desktop)

2. Create a new directory for your project and navigate to it using the terminal.

3. Create a new file named `Dockerfile` (without any file extension) in the project directory.

4. Open the `Dockerfile` in a text editor and copy the following content into it:

```Dockerfile
FROM node:lts-alpine

WORKDIR /app

# Dependencies
COPY package*.json ./
RUN npm ci

# Bundle
COPY . .
EXPOSE 3000

ENV PORT=3000

CMD ["node", "src/bin/www"]
```

5. Save the `Dockerfile`.

6. Open the terminal and navigate to the project directory.

7. Build a Docker image using the `Dockerfile` by running the following command:

```shell
docker build -t my-project .
```

The `-t` flag allows you to tag the image with a name (`my-project` in this example).

8. Once the image is built, you can run a Docker container using the following command:

```shell
docker run -p 3000:3000 my-project
```

The `-p` flag maps the container's port 3000 to the host's port 3000. You can change the host port if needed.

9. Access your project by opening a web browser and navigating to `http://localhost:3000`.

This process will build a Docker image based on the provided Dockerfile and run a container from that image. The container will have your project installed and running on port 3000.

Make sure to replace `my-project` with a suitable name for your project.

# run localy

To run your project locally without Docker, follow these instructions:

1. Make sure you have Node.js installed on your system. You can download and install Node.js from the official website: [Node.js](https://nodejs.org)

2. Open a terminal and navigate to the project directory.

3. Install the project dependencies by running the following command:

```shell
npm install
```

This command will install all the dependencies listed in the `package.json` file.

4. Once the dependencies are installed, you can start the project by running the following command:

```shell
npm start
```

This command will start the project and it will be accessible at `http://localhost:3000` in your browser.

If you want to specify a different port, you can set the `PORT` environment variable before running the command. For example:

```shell
PORT=8080 npm start
```

This will start the project on port 8080 instead of the default port 3000.

Make sure to replace `npm start` with the appropriate command if your project has a different start script defined in the `package.json` file.

These instructions will allow you to run your project locally without using Docker.
