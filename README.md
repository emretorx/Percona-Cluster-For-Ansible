# Ansbile 

apt install ansible -y
ansible-playbook -i inventory percona.yaml -l node

# Clustercheck user

CREATE USER 'clustercheckuser'@'localhost' IDENTIFIED BY 'clustercheckpassword!';
GRANT PROCESS ON *.* TO 'clustercheckuser'@'localhost' ;


