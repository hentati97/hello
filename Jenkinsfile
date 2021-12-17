pipeline {
   agent any
   stages {
       stage('Pull') {
           steps {
               script {
                   checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                   userRemoteConfigs:[[
                   url: 'https://github.com/hentati97/hello.git']]])
               }
           }
       }
       stage('Build') {
           steps {
               script {
               sh "sudo ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml "    
              	       }
           }
       }
       stage('Docker') {
           steps {
               script {
               sh "sudo ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml "    
              	       }
           }
       }
       stage('Push local image to repositroy') {
           steps {
               script {
               sh "sudo ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml "    
              	       }
           }
       }
   }
}
