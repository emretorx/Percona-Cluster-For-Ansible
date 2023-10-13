# Percona Cluster Setup with Ansible

In this guide, you will learn how to set up the Percona Cluster using Ansible.

## Prerequisites

- **Ansible Server**: 1 instance
- **Ubuntu 20 VMs**: 3 instances that the Ansible server can access via key authentication.

## Installation Steps

1. **Clone the Repository**
   
   ```bash
   git clone https://github.com/emretorx/Percona-Cluster-For-Ansibe.git
   ```

2. **Install Ansible**

   ```bash
   apt install ansible -y
   ```

3. **Modify Configurations**

   Adjust the IP addresses and passwords in `Percona-Cluster-For-Ansible/percona.yaml` and `Percona-Cluster-For-Ansible/inventory/nodes.yml` according to your environment.

4. **Run the Ansible Playbook**

   ```bash
   cd Percona-Cluster-For-Ansible
   ansible-playbook -i inventory percona.yaml -l node
   ```

5. **Create the Necessary User in MySQL**

   ```sql
   CREATE USER 'clustercheckuser'@'localhost' IDENTIFIED BY 'clustercheckpassword!';
   GRANT PROCESS ON *.* TO 'clustercheckuser'@'localhost';
   ```

6. **Restart HAProxy**

   First, use the `pcs status` command to identify on which node the floating IP is active:

   ```bash
   pcs status
   ```

   On the identified node, restart HAProxy:

   ```bash
   systemctl restart haproxy
   ```

With this guide, you can effortlessly set up the Percona Cluster. Happy installations!
