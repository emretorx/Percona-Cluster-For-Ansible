# Ansbile 

apt install ansible -y

ansible-playbook -i inventory percona.yaml -l node

# Clustercheck user

<pre><code>CREATE USER 'clustercheckuser'@'localhost' IDENTIFIED BY 'clustercheckpassword!'; </code></pre>

GRANT PROCESS ON *.* TO 'clustercheckuser'@'localhost' ;

