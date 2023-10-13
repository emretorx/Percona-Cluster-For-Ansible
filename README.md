# Percona Cluster Kurulumu için Ansible

Bu dökümanda, Percona Cluster'ı Ansible aracılığıyla nasıl kurabileceğinizi bulabilirsiniz.

## Ön Koşullar

- **Ansible Sunucusu**: 1 adet
- **Ubuntu 20 VM'ler**: Ansible sunucusunun anahtar (key) ile erişebileceği 3 adet.

## Kurulum Adımları

1. **Repo'yu Klonlayın**
   
   ```bash
   git clone https://github.com/emretorx/Percona-Cluster-For-Ansibe.git
   ```

2. **Ansible'ı Kurun**

   ```bash
   apt install ansible -y
   ```

3. **Konfigürasyonları Düzenleyin**

   `Percona-Cluster-For-Ansible/percona.yaml` ve `Percona-Cluster-For-Ansible/inventory/nodes.yml` içerisinde bulunan IP adresleri ve parolaların sizin ortamınıza uygun olacak şekilde düzenlenmesi gerekmektedir.

4. **Ansible Playbook'unu Çalıştırın**

   ```bash
   cd Percona-Cluster-For-Ansible
   ansible-playbook -i inventory percona.yaml -l node
   ```

5. **Mysql'da Gerekli Kullanıcıyı Oluşturun**

   ```sql
   CREATE USER 'clustercheckuser'@'localhost' IDENTIFIED BY 'clustercheckpassword!';
   GRANT PROCESS ON *.* TO 'clustercheckuser'@'localhost';
   ```

6. **HAProxy'yi Yeniden Başlatın**

   ```bash
   pcs status
   systemctl restart haproxy
   ```

Bu dökümanı kullanarak Percona Cluster kurulumunu kolayca gerçekleştirebilirsiniz. İyi kurulumlar!
