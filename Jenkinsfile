node() {
  try {
         stage (' Checkout ansible private repo') {
           dir ("private") {
           echo "Checking out private repo"
           git credentialsId: 'git',branch: params.private_repo_branch,url: 'https://github.com/ssksanthosh/cassandra-vars.git'
           var_path=pwd()
           echo "$var_path"
           }
        } 
                     
         stage ('Checkout ansible public repo') {
             echo "Checking out public repo"
             git branch: params.public_repo_branch,url: 'https://github.com/ssksanthosh/cassandra-demo.git'
        }
         
         stage ('Run playbook'){
             echo "Running playbook"
             echo "$var_path"
             sh "ansible-playbook -i ${var_path}/hosts main.yml --vault-password-file $JENKINS_HOME/secrets/vault-pass --check"
       }         
  } 
  catch (err)
    {
        throw err
    }
} 
    