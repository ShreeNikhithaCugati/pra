
pg-2


mvn --v
mkdir c2_batch
cd c2_batch
mvn archetype:generate -DgroupId=in.tcs -DartifactId=mvn_c2 -DarchetypeId=maven-archetype-quickstart -DarchetypeVersion=1.5 -DinteractiveMode=false
cd mvn_c2
mvn package 
java -cp target/mvn_c2-1.0-SNAPSHOT.jar in.tcs.App




prg -6



git config --global user.name "ShreeNikhithaCugati"
git config --global user.email "nikhucugati2005@gmail.com"
ssh-keygen -t ed25519 -C "nikhucugati2005@gmail.com"
git init
git add pom.xml
git add src
git commit -m "first"
git branch -M main
git remote add origin git@github.com:ShreeNikhithaCugati/pra.git
git remote set-url origin git@github.com:ShreeNikhithaCugati/pra.git
git push -u origin main
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

sudo update-alternatives --config java


pipeline {

agent any

stages {

stage('Checkout') {

steps {

git branch: 'main', url: 'https: //github.com/cmritsarada/exp6.git' // Replace with your repository URL

}}

stage('Build') {

steps {

sh 'mvn clean package'} }

stage('Test') {

steps {

sh 'mvn test'

} }}}




prg-7



hosts.ini=

[local]
localhost ansible_connection=local


ansible all -i hosts.ini --list-hosts
ansible all -i hosts.ini -m ping

gedit mypb.yml

 - name: First Playbook
   hosts: local
   connection: local
   tasks:
     - name: My first task
       debug:
         msg: "Ansible is a config mgmt_tool"
         
         
         
ansible-playbook -i hosts.ini mypb.yml
mkdir -p library
cd library

#!/usr/bin/python
from ansible.module_utils.basic import AnsibleModule

def run_module():
    module_args=dict(
        name=dict(type='str', required=True)
        )
        
    module= AnsibleModule(argument_spec=module_args)
    result= {"changed": False, "message": f"Hello,{module.params['name']}!"}
    module.exit_json(**result)
        
if __name__=='__main__':
     run_module()
     
     
  
cd ..
chmod +x library/first_module.py
gedit mypb2.yml


---
- name: Ansible with one module
  hosts: localhost
  gather_facts: no
  tasks:
   - name: Good Afternoon
     first_module: 
        name: "Ansible"
     register: result
   - name: Show message
     debug: 
        msg: "{{result.message}}"
        
        
        
prg-8======


sudo systemctl status jenkins
sudo update-alternatives --config java
sudo cat /var/lib/jenkins/secrets/initialAdminPassword  
     
cd c2_batch

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ShreeNikhithaCugati/pra.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: "**/target/*.jar", allowEmptyArchive: true
            }
        }

        stage('Deploy') {
            steps {
                sh """
                export ANSIBLE_HOST_KEY_CHECKING=False
                ansible-playbook -i hosts.ini mydeploy.yml --extra-vars='ansible_become_pass=exam@cse'
                """
            }
        }
    } // closes 'stages'
} // closes 'pipeline'


git branch
gedit hosts.ini 
gedit mydeploy.yml	


---
- name: Deploy Artifact to localhost
  hosts: localhost
  tasks:
    - name: Copy the artifact to the target location
      become: true
      become_user: student
      become_method: su
      copy:
        src: "/var/lib/jenkins/workspace/target/abc/mvn_c2-1.0-SNAPSHOT.jar"
        dest: "/home/student/p8.jar"

