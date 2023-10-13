# Ansible İle Percona Cluster Kurulumu

Bu kılavuzda, Percona Cluster'ın Ansible kullanılarak nasıl kurulacağını öğreneceksiniz.

## Ön Koşullar

- **Ansible Sunucusu**: 1 adet
- **Ubuntu 20 VM'ler**: Ansible sunucusunun anahtar (key) ile erişebileceği 3 adet.

## Kurulum Adımları

1. **Reposu Klonlayın**
   
   ```bash
   git clone https://github.com/emretorx/Percona-Cluster-For-Ansibe.git
   ```

2. **Ansible'ı Yükleyin**

   ```bash
   apt install ansible -y
   ```

3. **Konfigürasyonları Düzenleyin**

   `Percona-Cluster-For-Ansible/percona.yaml` ve `Percona-Cluster-For-Ansible/inventory/nodes.yml` dosyalarındaki IP adreslerini ve parolalarını kendi ortamınıza göre ayarlayın.

4. **Ansible Playbook'unu Çalıştırın**

   ```bash
   cd Percona-Cluster-For-Ansible
   ansible-playbook -i inventory percona.yaml -l node
   ```

5. **MySQL'de Gerekli Kullanıcıyı Oluşturun**

   ```sql
   CREATE USER 'clustercheckuser'@'localhost' IDENTIFIED BY 'clustercheckpassword!';
   GRANT PROCESS ON *.* TO 'clustercheckuser'@'localhost';
   ```

6. **HAProxy'yi Yeniden Başlatın**

   Öncelikle `pcs status` komutu ile floating IP'nin hangi node'da olduğunu tespit edin:

   ```bash
   pcs status
   ```

   Tespit ettiğiniz node'da HAProxy'yi yeniden başlatın:

   ```bash
   systemctl restart haproxy
   ```

Bu kılavuzu kullanarak Percona Cluster kurulumunu kolaylıkla gerçekleştirebilirsiniz. Başarılı kurulumlar dileriz!
