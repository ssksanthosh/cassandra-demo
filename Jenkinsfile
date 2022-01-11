pipeline {
    agent any
        stages {
            stage ('Checkout Ansible public repo') {
              steps {
                echo "Checking out public repo"
                git branch: 'main',url: 'https://github.com/ssksanthosh/nginx-demo.git'
              }
            }  
             stage (' Run Ansible playbook') {
              steps {
                echo "Running playbook"
                sh 'ansible-playbook nginx.yml --check'
              } 
           }
        }   
}    
    