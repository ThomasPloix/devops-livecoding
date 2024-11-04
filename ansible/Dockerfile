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

# Copy all contents in the /ansible directory (including inventories, roles, playbooks)
COPY . /ansible

# Set environment variables, if needed
ENV ANSIBLE_HOST_KEY_CHECKING=False

# Default entrypoint for running Ansible commands
ENTRYPOINT ["ansible-playbook"]
CMD ["playbook.yml", "-i", "inventories/setup.yml"]
