- First Remove softs on your OS

sudo apt-get purge nginx*
sudo apt-get remove nginx*
sudo apt-get purge mysql*
sudo apt-get remove mysql*
sudo apt-get purge php-fpm
sudo apt-get remove php-fpm

- Requires Ansible 2.0 or newer (in ubuntu 14 or older install by pip install)
- for run: sudo ansible-playbook -i hosts playbook.yml
- I have already test on Ubuntu 16.0.4 LTS

- The playbooks will configure Mariadb, WordPress, Nginx, and PHP-FPM. When the run
  is complete, you can hit access www.quyet.local

