CI/CD Pipeline with Docker, Jenkins, and a Web App
Containerize a simple web application(HTML+nginx)
WEB APP
index.html,it simply create normall indxe web page
docker build -t my-web-app .
This created an image named my-web-app
ocker run -d -p 8080:80 my-web-app
-d → Runs the container in detached mode (in the background).
-p 8080:80 → Maps port 8080 on your local machine to port 80 inside the container so that we can access the web app in the browser at http://localhost:8081.
then Docker file
# Use the official Nginx image as the base
FROM nginx:latest
FROM nginx:latest → Uses the official Nginx Docker image as the base image.

This means we don't need to install Nginx manually—it's already included in this image.

# Copy the HTML file to the Nginx default directory
COPY index.html /usr/share/nginx/html/index.html
COPY index.html /usr/share/nginx/html/index.html → Copies our index.html file inside the container to the Nginx default web directory.

This ensures that when Nginx starts, it serves our custom HTML file instead of the default Nginx page.
# Expose port 80
EXPOSE 80
EXPOSE 80 → Tells Docker that our container will listen for incoming traffic on port 80.

However, this does not automatically publish the port; that's why we need -p in docker run.

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
CMD ["nginx", "-g", "daemon off;"] → Runs Nginx when the container starts.

daemon off; ensures that Nginx runs in the foreground instead of the background (so that the container keeps running).