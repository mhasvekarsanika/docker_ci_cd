# Use the official Jenkins LTS image as the base
FROM jenkins/jenkins:lts  

# Switch to root user to install dependencies
USER root  

# Install Docker inside the Jenkins container (so Jenkins can build Docker images)
RUN apt-get update && apt-get install -y docker.io  

# Give Jenkins user permission to use Docker
RUN usermod -aG docker jenkins  

# Switch back to Jenkins user
USER jenkins  

# Expose Jenkins default port
EXPOSE 8080  

# Start Jenkins correctly
ENTRYPOINT ["/usr/bin/tini", "--", "/usr/local/bin/jenkins.sh"]