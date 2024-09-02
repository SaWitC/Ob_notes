Key concepts and components
- **Container** lightweight standalone and executable packages of software that include everything needed to run a piece of software, such as the code ,runtime, libraries and configuration. Containers share the host system kernel and resources which makes them more efficient than traditional VM

- **Images** Read-only templates used to create containers. An image include application code and dependencis and can be build by **Dockerfile**

- **Dockerfile** a script that contains all command to build an image (and it allows user to automate the image creation process).

- **Docker engine** Docker engine the runtime that enables containers to run on a host operating system it consist of
	1. Docker Deamond: the background service running on the host that manages Docker images, Containers, Networks, and storage volumes.
	2. Docker CLI the command-line interface used to interact with the docker Deamond

- **Docker Hub**: A cloud-based registry service for storing and distributing Docker images. Users can upload their own images or use images created by others.

- **Volumes** storage units that can be attached to containers allowing data to persist outside the container lifecycle.
## Commands :
Docker build - create a docker image from docker file
Docker run - start a container from the image

WORKDIR /src
The `WORKDIR` instruction sets the working directory for any subsequent `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, and `ADD` instructions in the Dockerfile.
- **Purpose**: To set the default directory where commands will be executed.
- **Effect**: If the directory `/src` does not exist, it will be created. All subsequent commands will be run from this directory, unless another `WORKDIR` instruction is encountered later in the Dockerfile.
- **Example**: After setting `WORKDIR /src`, a command like `COPY . .` will copy files into `/src`.

COPY
The `COPY` instruction copies new files or directories from the source and adds them to the filesystem of the container at the specified destination.

- **Syntax**: `COPY [<src>,... <dest>]`
    - `<src>`: Source file(s) or directory(ies) relative to the build context.
    - `<dest>`: Destination path inside the container.
- **Purpose**: To copy specific files or directories from the build context (the directory where the Docker build command is run) to the container's filesystem.
- **Effect**: The specified file (`Diflexmo.Forwarding.API.Host.csproj`) is copied from the `Diflexmo.Forwarding.API.Host` directory in the build context to the same directory structure inside the container.