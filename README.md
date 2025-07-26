# FogCast

FogCast is a project developed as part of the 2024/25 Master of Computer Science program at HTWG Konstanz. It focuses on analyzing, evaluating, and presenting weather data for the Lake Constance region. The project aims to improve the understanding of weather phenomena, such as fog, and enhance forecasting accuracy.

## Getting Started with Development

### Prerequisites

1. **Git Submodules**:
   - This project uses Git submodules. To initialize and update them, run:
     ```bash
     git submodule update --init --recursive
     ```

2. **Ansible**:
   - Ensure you have Ansible installed. You can install it using pip:
     ```bash
     pip install ansible
     ```
   - Ansible is used for automating deployment and configuration tasks.

3. **Docker**:
   - Install Docker and Docker Compose to manage containerized services.

### Setting Up the Project

1. Clone the repository:
   ```bash
   git clone --recurse-submodules <repository-url>
   ```

2. Navigate to the project directory:
   ```bash
   cd FogCast
   ```

3. Initialize and update submodules (if not done during cloning):
   ```bash
   git submodule update --init --recursive
   ```

### Development Workflow

- **Frontend**:
  - Navigate to the `Visualization` directory and install dependencies:
    ```bash
    cd Visualization
    npm install
    ```
  - Start the development server:
    ```bash
    npm run dev
    ```

- **Backend**:
  - Navigate to the `Data-Interface` directory and set up the Python environment:
    ```bash
    cd Data-Interface
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    pip install -r requirements.txt
    ```
  - Run the backend service:
    ```bash
    python backend/app.py
    ```

- **Cronjob Service**:
  - Navigate to the `Cronjob-Service` directory and set up the Python environment:
    ```bash
    cd Cronjob-Service
    python -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt
    ```
  - Run a specific cron job:
    ```bash
    python bin/main.py run_single_job_now=<cronjob_class_name>
    ```

## Deployment

Deployment is managed using Ansible. The playbooks are located in the `ansible` directory.
There are separate inventories for development and production environments.

Before deploying, ensure you have the `inventories/dev/hosts.ini` and `inventories/prod/hosts.ini` files configured with the appropriate server details.
The template for the hosts file is the following:
```ini
[app_servers]
dev-server ansible_host=<<IP>> ansible_user=<<USER>>
```

To deploy the application to the development environment, run:
```bash
ansible-playbook -i ansible/inventories/dev/hosts.ini ansible/playbook.yml
```

To deploy to the production environment, use:
```bash
ansible-playbook -i ansible/inventories/prod/hosts.ini ansible/playbook.yml
```
