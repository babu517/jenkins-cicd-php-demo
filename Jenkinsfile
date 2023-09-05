pipeline {
    agent any
  
       stages {
        stage('git clone'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/babu517/jenkins-cicd-php-demo.git']]])
            }
        }
       stage('Execute Playbook'){
           steps{
               ansiblePlaybook credentialsId: 'private-key', disableHostKeyChecking: true, installation: 'ansible2', inventory: 'dev.inv', playbook: 'deploy.yaml'
           }
       }
    }
}
