pipeline {
    agent any
    
     parameters {
     choice choices: ['qa', 'production', 'cloud'], description: 'Select environment for deployment', name: 'DEPLOY_TO'

    string(name: 'upstreamJobName',
          defaultValue: '',
          description: 'The name of the job the triggering upstream build'
    )
    }
    
    stages {
       stage('Copy Artifact') {
            steps {
                  archiveArtifacts artifacts: 'main.rb', followSymlinks: false
            }
        }

       stage('Deliver') {
          steps {
            sshagent(['vagrant-private-key']) {
          sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i ${DEPLOY_TO}.ini playbook.yml'
            }
         }
       }
       
       
    }
}
