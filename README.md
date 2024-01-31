# Ansible İle Percona Cluster Kurulumu

Bu kılavuzda, Percona Cluster'ın Ansible kullanılarak nasıl kurulacağını öğreneceksiniz.

## Ön Koşullar

- **Ansible Sunucusu**: 1 adet
- **Ubuntu 22 VM'ler**: Ansible sunucusunun anahtar (key) ile erişebileceği 3 adet.

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

Bu kılavuzu kullanarak Percona Cluster kurulumunu kolaylıkla gerçekleştirebilirsiniz. Başarılı kurulumlar dileriz!
