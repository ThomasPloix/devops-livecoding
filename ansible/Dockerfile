# Use an official lightweight Python image as the base
FROM python:3.10-slim

# Install Ansible and other dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    sshpass \
    openssh-client \
    git && \
    pip install --no-cache-dir ansible && \
    rm -rf /var/lib/apt/lists/*

# Set the working directory inside the container
WORKDIR /ansible

# Copy your Ansible playbooks, inventories, and other configurations into the container
COPY . .

# Set environment variables, if needed
ENV ANSIBLE_HOST_KEY_CHECKING=False

# Run Ansible command by default (adjust based on your needs)
ENTRYPOINT ["ansible-playbook"]
