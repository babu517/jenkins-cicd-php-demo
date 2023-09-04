pipeline {
    agent any

    environment {
        ANSIBLE_HOME = tool name: 'ansible2', type: 'Tool'
    }
       stages {
        stage('git clone'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/babu517/jenkins-cicd-php-demo.git']]])
            }
        }
       stage('Execute Playbook'){
           steps{
               ansiblePlaybook credentialsId: 'private-key', disableHostKeyChecking: true, installation: "${ANSIBLE_HOME}", inventory: 'dev.inv', playbook: 'deploy.yaml'
           }
       }
    }
}
