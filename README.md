vi inventory.ini

ansible all -i inventory.ini -m ping
vi install_htop.yml
 Add the following content:
 
 ---
- name: Install htop system monitor tool
 hosts: local
 become: true
 
 tasks:
 - name: Install htop package
 ansible.builtin.package:
 name: htop
 state: present

ansible-playbook -i inventory.ini install_htop.yml


java -cp target/myapp-1.0-SNAPSHOT.jar com.example.App
