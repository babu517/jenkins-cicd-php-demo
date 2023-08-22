pipeline {
    agent any
    stages {
        stage('git clone'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/babu517/jenkins-cicd-php-demo.git']]])
            }
        }
    stage('Copy files to Target Host'){
        steps{
    sshagent(['jenkins-ec2-user-raj']) {
       sh 'ssh -o StrictHostKeyChecking=no root@ip-182.18.184.78'
       sh 'scp -rp /var/lib/jenkins/workspace/demo-php-github/* ubuntu@ip-172-31-5-131:/var/www/html/'
    }
         }
    }
}
}

