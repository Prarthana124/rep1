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

888888

mkdir ansible-lab
 cd ansible-lab
 vi inventory.ini 
 Add the following into the Inventory file 
 [local]
 localhost ansible_connection=local
 Create the deploy.yml playbook:
 ---
 - name: Deploy JAR
 hosts: local
 become: true
 
 tasks:
 - name: Copy JAR file
 copy:
 src: /mnt/c/ProgramData/Jenkins/.jenkins/workspace/your-job/target/your-app.jar
 dest: /home/your-username/ansible-lab/app.jar
 mode: '0755'
 
 - name: Run JAR file
 shell: nohup java -jar /home/your-username/ansible-lab/app.jar > app.log 2>&1 &
Step 3. Run the Playbook manually in WSL to verify the deployment:
 ansible-playbook -i inventory.ini deploy.yml


cat app.log
