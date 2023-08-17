# Ansbile 

<pre><code>apt install ansible -y</code></pre>

<pre><code>ansible-playbook -i inventory percona.yaml -l node </code></pre>

# Clustercheck user

<pre><code>CREATE USER 'clustercheckuser'@'localhost' IDENTIFIED BY 'clustercheckpassword!'; </code></pre>

<pre><code>GRANT PROCESS ON *.* TO 'clustercheckuser'@'localhost';</code></pre>

