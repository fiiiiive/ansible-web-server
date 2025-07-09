# Ansible Azure Web Server Project

This is a project I built to learn how to automate creating and managing an Azure VM with Ansible. It sets up a basic web server (Nginx), lets me start and stop the VM, and helped me practice working with infrastructure as code.

---

## What This Project Does

- Creates an Azure virtual machine
- Installs and configures Nginx
- Starts and stops the VM when needed
- Tests Azure authentication and setup
- Keeps everything organized in Ansible roles and playbooks

---

## Project Structure

```

NEWANSIBLEWEBSERVER/
├── inventory.ini          # Inventory file for Ansible
├── site.yml               # Main playbook
├── test\_azure.yml         # Checks Azure login and credentials
├── start\_vm.yml           # Starts the VM
├── stop\_vm.yml            # Stops the VM
├── roles/
│   └── webserver/
│       ├── tasks/
│       │   └── main.yml
│       ├── handlers/
│       │   └── main.yml
│       ├── templates/
│       │   └── index.html.j2
│       └── vars/
│           └── main.yml
├── venv/                  # Python virtual environment (ignored)
├── .gitignore             # Ignores sensitive files

````

---

## How to Use It

1. Set up a virtual environment

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install ansible
````

Make sure you also install Azure-related Python packages.

2. Fill out `inventory.ini`

   Put your VM's IP address and SSH user in there.

3. Run playbooks

   Start the VM:

   ```bash
   ansible-playbook start_vm.yml
   ```

   Stop the VM:

   ```bash
   ansible-playbook stop_vm.yml
   ```

   Configure everything:

   ```bash
   ansible-playbook site.yml
   ```

4. Check your Azure setup

   ```bash
   ansible-playbook test_azure.yml
   ```


## What I Learned

This project taught me how to:

* Create and manage VMs in Azure
* Automate server setup with Ansible
* Use templates to generate configuration files
* Handle VM power states (start, stop, deallocate)
* Keep secrets out of Git using `.gitignore`
* Deal with Python virtual environments and package dependencies
* Debug Ansible errors and dependency issues

---

## How It Handles Sensitive Stuff

* The `.gitignore` makes sure things like `venv/`, `inventory.ini`, and variables don’t get committed.
* No real credentials or SSH keys are included here.
* You can use Ansible Vault later if you want even more security.

---

## Ideas for Future Improvements

* Encrypt secrets with Ansible Vault
* Add CI/CD workflows (like GitHub Actions) to run playbooks automatically
* Make variables (region, VM size, etc.) configurable
* Create extra roles for other services
