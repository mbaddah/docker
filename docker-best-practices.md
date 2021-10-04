## Good practices:

- Tag images rather than use id

- Split COPY so that install dependencies first, followed by COPYing project files, else will always download install all dependencies even if nothing has changed.

- Why create separate docker containers for Node + Redis rather than a combined container which installs Node + Redis? Loose coupling + scalability.

- Use docker-compose to start multiple containers and automate common CLI commands. Simplifies networking by creating containers in same network.

- Use Docker volume as a reference (pointer-like) to map container folders back to host. 