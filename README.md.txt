

    # Ansible Playbook for Docker InstallationThis Ansible playbook automates the installation of Docker and Docker Compose on `ec2-server`.## Requirements- Ansible- `ec2-server` inventory entry in your Ansible inventory file.## Usage1. Update your Ansible inventory file to include `ec2-server` with the appropriate IP or hostname.2. Run the following command to execute the Ansible playbook:   ```shell   ansible-playbook playbook.yaml

Replace `playbook.yaml` with the name of your playbook file.

## Playbook Steps

1.  Install Docker:

    *   Use `dnf` module to install Docker package.
    *   Ensure the Docker package is present and up to date.

2.  Install Docker Compose:

    *   Use `get_url` module to download the Docker Compose binary from the official GitHub releases.
    *   Specify the destination path as `/usr/local/bin/docker-compose`.

3.  Start Docker Daemon:

    *   Use the `systemd` module to start the Docker service.

4.  Add `ec2-user` to Docker group:

    *   Use the `user` module to add `ec2-user` to the `docker` group.
    *   The user is appended to the group, allowing them to run Docker commands.

5.  Reconnect to Server Session:

    *   Use the `meta` module with `reset_connection` argument to reconnect to the server session.

6.  Install Docker Python Module:

    *   Use the `pip` module to install the Docker Python module.
    *   Specify the executable path as `/usr/bin/pip3`.

7.  Pull Redis Docker Image:

    *   Use the `docker_image` module to pull the Redis Docker image.

<!---->

    Please note that you might need to modify the playbook file name and adjust the inventory file according to your specific setup. Additionally, make sure you have the necessary permissions and configurations in place to run Ansible playbooks.Hope this helps!
