# STEP 1: Use the official, lightweight Nginx Alpine image as the base
FROM nginx:alpine

# STEP 2: Copy the local static website file into the default Nginx public directory
COPY index.html /usr/share/nginx/html/index.html

# STEP 3: Document that the container listens on port 80 at runtime
EXPOSE 80