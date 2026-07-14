# DevOps & Cloud Engineering - Module 1: Linux & Docker

This document serves as a comprehensive reference guide for Linux system administration, Git workflows, Docker containerization, Docker Compose orchestration, and automation.

---

## 🐧 BLOCK 1: ESSENTIAL LINUX NAVIGATION & FILE OPERATIONS
> 💡 Command Line Interface (CLI) is the primary tool for managing cloud infrastructure.
* `pwd` - Print Working Directory (shows exactly where you are in the filesystem).
* `ls -la` - List directory contents (shows all files, including hidden ones, with detailed permissions and sizes).
* `cd <directory>` - Change Directory (navigate to a specific folder).
* `mkdir -p <path>` - Create a directory (and any necessary parent directories) if they do not exist.
* `touch <filename>` - Create an empty file or update the timestamp of an existing file.
* `cp <source> <destination>` - Copy files or directories.
* `mv <source> <destination>` - Move or rename files or directories.
* `rm -rf <path>` - Recursively and forcefully remove files or directories (use with caution!).

---

## 📄 BLOCK 2: VIEWING & EDITING FILES IN LINUX
> 💡 Reading and modifying configuration files directly from the terminal.
* `cat <file>` - Display the entire content of a file in the terminal.
* `less <file>` - Open a file in an interactive, scrollable viewer (press `q` to exit).
* `head -n <number> <file>` - View the first N lines of a file.
* `tail -f <file>` - Output the last part of a file and monitor real-time changes (essential for reading logs).
* `nano <file>` - Open a simple, user-friendly text editor inside the terminal.

---

## 🔒 BLOCK 3: USER MANAGEMENT & PERMISSIONS
> 💡 Security first: Managing file access rights and superuser privileges.
* `sudo <command>` - Execute a command with administrative (root) privileges.
* `chmod +x <file>` - Make a file executable (allows running it as a script).
* `chmod 600 <file>` - Set read/write permissions for the owner only (commonly used for SSH keys).
* `chown <user>:<group> <file>` - Change the owner and group ownership of a file or directory.

---

## ⚡ BLOCK 4: PROCESS MANAGEMENT & SYSTEM MONITORING
> 💡 Keeping track of system resources, CPU, memory, and running applications.
* `ps aux` - Snapshot of all currently running processes in the system.
* `top` / `htop` - Interactive, real-time system resource and process monitor.
* `kill -9 <PID>` - Forcefully terminate a process using its Process ID.
* `df -h` - Display free and used disk space on mounted filesystems in human-readable format.
* `free -h` - Display total, used, and available physical memory (RAM).

---

## 🌐 BLOCK 5: NETWORKING & TROUBLESHOOTING
> 💡 Diagnosing network connections and verifying open ports.
* `ip a` - Show all network interfaces and assigned IP addresses.
* `ping <host>` - Send ICMP ECHO_REQUEST packets to network hosts to test connectivity.
* `curl -I <URL>` - Fetch the HTTP headers of a webpage to verify server status.
* `netstat -tuln` / `ss -tuln` - List all active listening ports (TCP and UDP) on the system.

---

## 📦 BLOCK 6: PACKAGE MANAGEMENT (APT)
> 💡 Installing, updating, and managing software packages on Debian/Ubuntu systems.
* `sudo apt update` - Update the local index of available packages from remote repositories.
* `sudo apt upgrade -y` - Upgrade all installed packages to their latest versions.
* `sudo apt install <package> -y` - Download and install a specific software package.
* `sudo apt remove <package>` - Uninstall a package while keeping its configuration files.

---

## 🗂️ BLOCK 7: ARCHIVING & COMPRESSION
> 💡 Packaging multiple files together for backups or transfers.
* `tar -czvf archive.tar.gz <directory>` - Compress a directory into a `.tar.gz` archive.
* `tar -xzvf archive.tar.gz` - Extract a compressed `.tar.gz` archive to the current directory.
* `zip -r archive.zip <directory>` - Compress files/folders into a `.zip` file.
* `unzip archive.zip` - Extract a `.zip` archive.

---

## 🛠️ BLOCK 8: ENVIRONMENT VARIABLES & PATH
> 💡 Configuring system-wide and user-specific variables.
* `export VAR_NAME="value"` - Set a temporary environment variable for the current session.
* `echo $VAR_NAME` - Print the value of an environment variable.
* `env` - List all currently active environment variables.
* `~/.bashrc` - User configuration file where persistent environment variables and aliases are defined.

---

## 🐙 BLOCK 9: GIT & GITHUB WORKFLOW (GIT FLOW)
> 💡 Industry-standard collaborative development and version control.
* `git checkout -b <branch>` - Create and switch to a new development branch.
* `git status` - Show the working tree status (untracked, modified, or staged files).
* `git add .` - Stage all current changes for the next commit.
* `git commit -m "prefix(scope): message"` - Record staged changes to repository history (using Conventional Commits).
* `git push -u origin <branch>` - Push local branch to GitHub and set up remote tracking.
* `git pr` (Custom Alias) - Automatically pushes the current branch and creates a GitHub Pull Request using GitHub CLI (`gh`).

---

## 🐳 BLOCK 10: DOCKER FUNDAMENTALS & CONTAINER LIFE CYCLE
> 💡 Packaging applications into isolated, portable, lightweight runtimes.
* `docker run -d -p <host-port>:<container-port> --name <name> <image>` - Run a container in detached mode with port mapping.
* `docker ps -a` - List all running and stopped containers.
* `docker stop <container>` - Stop a running container gracefully.
* `docker rm <container>` - Remove a stopped container from the host system.
* `docker logs -f <container>` - Fetch and stream real-time logs of a specific container.
* `docker exec -it <container> sh` - Open an interactive shell inside a running container.

---

## 🏗️ BLOCK 11: CUSTOM IMAGE CREATION (DOCKERFILE)
> 💡 Defining application blueprints to build repeatable and standardized images.
* `FROM` - Set the base image for subsequent instructions (e.g., `nginx:alpine`).
* `COPY <src> <dest>` - Copy files or directories from the host machine into the container's filesystem.
* `EXPOSE <port>` - Document the port on which the container will listen at runtime.
* `docker build -t <tag-name> .` - Build a custom Docker image using the Dockerfile in the current directory.

---

## 🐙 BLOCK 12: MULTI-CONTAINER ORCHESTRATION WITH DOCKER COMPOSE
> 💡 Defining and running multi-container applications using a single YAML configuration file.
* `docker compose up -d` - Build, (re)create, start, and run containers for services defined in `docker-compose.yml` in detached mode.
* `docker compose down` - Stop and remove containers, networks, volumes, and images created by `up`.
* `docker compose ps` - List all containers associated with the current Compose project and their statuses.

---

## 💾 BLOCK 13: PERSISTENT DATA WITH DOCKER VOLUMES & BIND MOUNTS
> 💡 Sharing directories and files dynamically between the host machine (Ubuntu) and the container.
* `Bind Mount` - Direct mapping of a specific, existing path on the host to a path inside the container. Ideal for real-time code development.
* `docker run -v /host/path:/container/path` - Mount a directory using the legacy run command.
* In Docker Compose: Defined under the `volumes:` key for a specific service to synchronize code and persist data.

---

## 🌐 BLOCK 14: ISOLATED CONTAINER NETWORKING (DOCKER NETWORKS)
> 💡 Docker Networks allow isolated containers to communicate with each other securely using internal DNS resolution.
* `Bridge Network` - The default network driver. Containers on the same custom bridge network can talk to each other using their service/container names as hostnames.
* `Isolation` - Databases or backend services can remain completely hidden from the host machine (no ports exposed to the outside world), while frontend apps in the same network can still access them internally.

---

## 📊 BLOCK 15: MULTI-CONTAINER MONITORING & LOG MANAGEMENT
> 💡 Essential commands for debugging and observing active multi-container environments.
* `docker compose stats` - Displays a live, real-time resource usage stream (CPU, Memory, Network I/O) for all containers in the stack.
* `docker compose logs -f` - Streams aggregated, color-coded live logs from all services in the compose file simultaneously.