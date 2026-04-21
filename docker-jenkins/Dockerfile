FROM jenkins/jenkins:latest

# Switch to root user temporarily to install additional dependencies if needed
USER root

# Example: Install basic packages (optional)
RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# The Jenkins base image already defines /var/jenkins_home as a volume by default,
# but we declare it explicitly as a best practice
VOLUME /var/jenkins_home

# Switch back to the default jenkins user
USER jenkins
