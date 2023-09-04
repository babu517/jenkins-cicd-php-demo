pipeline {
    agent any
    tool {
        maven 'maven3'
    }
    stages {
        stage('git clone'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/babu517/jenkins-cicd-php-demo.git']]])
            }
        }
        stage('Maven Build'){
            steps{
                sh "mvn clean install"
            }
        }
        stage('Deploy') {
            steps {
                script {

                // Define your Ansible playbook command
                    def ansiblePlaybookCommand = """
                        ansible-playbook -i dev.inv deploy.yaml
                    """
                    // Execute the Ansible playbook command
                // Run Ansible playbook to deploy the application
                sh 'ansible-playbook -i dev.inv deploy.yaml'
            }
        }
     }
}
}
