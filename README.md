# Ansbile 

apt install ansible -y

ansible-playbook -i inventory percona.yaml -l node

# Clustercheck user
```sql
CREATE USER 'clustercheckuser'@'localhost' IDENTIFIED BY 'clustercheckpassword!'; ```

```sql
GRANT PROCESS ON *.* TO 'clustercheckuser'@'localhost' ;

