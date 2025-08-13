# FogCast

FogCast is a project developed as part of the 2024/25 Master of Computer Science program at HTWG Konstanz. It focuses on analyzing, evaluating, and presenting weather data for the Lake Constance region. The project aims to improve the understanding of weather phenomena, such as fog, and enhance forecasting accuracy.

## Getting Started with Development

### Prerequisites

1. **Ansible**:
   - Ensure you have Ansible installed. You can install it using pip:
     ```bash
     pip install ansible
     ```
   - Ansible is used for automating deployment and configuration tasks.

2. **Docker**:
   - Install Docker and Docker Compose to manage containerized services.

### Setting Up the Project

1. Clone the repository:
   ```bash
   git clone https://github.com/FogCast-Konstanz/FogCast.git 
   ```

2. Navigate to the project directory:
   ```bash
   cd FogCast
   ```

### Other Repositories

The other repositories, that are part of this project are:

- [**Cronjob-Service**](https://github.com/FogCast-Konstanz/Cronjob-Service.git): The repository that holds the implementation of the cronjobs used to gather and preprocess weather information.

- [**Visualization**](https://github.com/FogCast-Konstanz/Visualization.git): The frontend of our website is developed in React. 

- [**Data-Interface**](https://github.com/FogCast-Konstanz/Data-Interface.git): The backend is written in Python using Flask.

- [**Infrastructure**](https://github.com/FogCast-Konstanz/Infrastructure.git): The infrastructure repository holds the config for the reverse proxy and InfluxDB containers.

- [**Weatherstation-Services**](https://github.com/FogCast-Konstanz/weatherstation-sevices.git): This repository holds the code of the services that run on our weatherstation at the HTWG-Konstanz.

- [**Models-and-Forecasting**](https://github.com/FogCast-Konstanz/models-and-forecasting.git): This repository focuses on quantifying model performance and improving forecast quality. Vision of creating a own FogCast ensemble model for better forecasting performance in Constance.

## Deployment

Deployment is managed using Ansible. The playbooks are located in the `ansible` directory.
There are separate inventories for development and production environments.

Before deploying, ensure you have the `inventories/dev/hosts.ini` and `inventories/prod/hosts.ini` files configured with the appropriate server details.
There is an example file which is called `inventories/dev/hosts.example.ini` which has to be renamed to `hosts.ini` and changed accordingly.

To deploy the application to the development environment, run:
```bash
ansible-playbook -i ansible/inventories/dev/hosts.ini ansible/playbook.yml
```

To deploy to the production environment, use:
```bash
ansible-playbook -i ansible/inventories/prod/hosts.ini ansible/playbook.yml
```
