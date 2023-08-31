pipeline {
    agent any
    stages {
        stage('git clone'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/babu517/jenkins-cicd-php-demo.git']]])
            }
        }
    stage('Deploy') {
            steps {
                // Run Ansible playbook to deploy the application
                sh 'ansible-playbook -i "https://github.com/babu517/jenkins-cicd-php-demo/blob/main/deploy.yaml" /etc/ansible/hosts'
            }
        }
}

}
