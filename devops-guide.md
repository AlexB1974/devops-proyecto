name: DevOps Workflow

on:
  push:
    branches: [ master ]

jobs:
  provision:
    name: Provision Infrastructure
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v3

    - name: Set up Terraform
      uses: hashicorp/setup-terraform@v2

    - name: Initialize Terraform
      working-directory: terraform
      run: terraform init

    - name: Apply Terraform
      working-directory: terraform
      run: terraform apply -auto-approve

  configure:
    name: Configure EC2 with Ansible
    needs: provision
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v3

    - name: Install Ansible
      run: |
        sudo apt update
        sudo apt install -y ansible

    - name: Run Ansible Playbook
      working-directory: ansible
      run: ansible-playbook setup.yml -i inventory

  deploy:
    name: Deploy with Docker
    needs: configure
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v3

    - name: Install Docker
      run: |
        sudo apt update
        sudo apt install -y docker.io
        sudo systemctl start docker

    - name: Run Docker Compose
      working-directory: pipeline
      run: docker-compose up -d
