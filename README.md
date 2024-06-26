Learning Docker

A Dockerfile is a script that contains instructions for building a customized docker image. Each instruction in a Dockerfile creates a new layer in the image, and the final image is composed of all the layers stacked on top of each other.

Docker File Building from Scratch

1. FROM

    The FROM instruction specifies the base image that the container will be bult on top of. This instruction is typically the first one in a Dockerfile and is used to set the base image for the container. The format of the instruction is:

    FROM /<image/>

    Ex: FROM node:14-alpine3.16

    This instruction tells Docker to use the node:14-alpine3.16 image as the base image for the container. To use a specific version or tag of an image you can use: /<version/> or:/<tag/> syntax.

2. WORKDIR

    In a Dockerfile, the WORKDIR instruction sets the working directory for any command that follows it in the Dockerfile. This means that any commands that are run in the container will be executed relative to the specified directory. Below is the format of the instruction :

    WORKDIR /<directory/>

    Ex: WORKDIR /app

    This instruction tells Docker to set the working directory of the container to /app . Any subsequent commands in the Dockerfile, such as COPY, RUN, or CMD, will be executed in this directory.

    It’s important to note that the WORKDIR instruction creates the directory if it does not already exist. And the subsequent COPY and ADD commands will be executed relative to the WORKDIR specified.

3. COPY

    Use the COPY instruction to copy local files from the host machine to the current working directory. For example, to copy a file named package.json from the host machine’s current directory to the image’s /app directory, you would use the following command:

    COPY package.json /app/

    If you want to copy all the files from the host’s current directory to the container’s current directory, you can use the below command:

    COPY . .

    It is used to copy all files and directories from the current directory on the host machine (indicated by “.”) to the current directory within the container.

    The first “.” refers to the source directory on the host machine, and the second “.” refers to the destination directory within the container.


4. RUN

    Use the “RUN” instruction to execute commands that will run during the image build process.

    RUN /<command_name/>

    For example, to update the package manager and install a specific package, you would use the following command:

    RUN npm install

5. CMD

    In a Dockerfile, the CMD instruction sets the command that will be executed when a container is run from the image. The format of the instruction is:

    CMD ["executable","param1","param2",...]

    Ex: CMD ["npm", "start"]

    This instruction tells Docker to run the command npm start when a container is created from the image. This command will start the Node.js application that was installed in the container using the npm install command.


-> Apart from all the instructions mentioned, there are some more instructions like ENV, and EXPOSE which are also used in creating Dockerfile. Below is a detailed description of the same:

6. ENV

    Use the ENV instruction to set environment variables inside the image which will be available during build time as well as in a running container. For example, to set the NODE_ENV environment variable to production, you would use the following command:

    ENV NODE_ENV production

7. EXPOSE

    Use the EXPOSE command to tell Docker which ports the container will listen on at runtime. For example, if your application listens on port 9000, you would use the following command:

    EXPOSE 9000

Build Docker Image

    docker build -t <image_name>

    "-t" is used for tag name.

Verify Docker Image

    docker images

Tag the imagename sing this command

    docker tag imagename:tag username/imagename:tag

    Ex: docker tag testing:v1 username/testing:v1

Push the image

    docker push username/imagename:tag

    Ex: docker push username/testing:v1

    > OR you can use the below command to push without providing the username.

    docker push imagename:tag

    Ex: docker push testing:V1

Run Docker Image

    docker run <image_name>:<tag_name>












