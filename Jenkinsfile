// Jenkinsfile

pipeline{
    agent any

    stages {
        stage('Git Checkout'){
            steps{
                git branch: 'master', url: 'https://github.com/maazpatel24/Jenkins-Terraform-SonarCloud.git'
            }
        }

        stage('Script'){
            steps{
                sh "echo Hello World"
                sh "ls; pwd"
            }
        }
    }
}