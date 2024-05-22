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

        stage('Terraform Initialization'){
            steps{
                sh "pwd"
                dir('Infra'){
                    sh "pwd"
                }
                sh "cd Infra; ls"
                // sh "terraform init"
            }
        }

        stage('SonarQube analysis') {
          steps {
            script {
                scannerHome = tool 'SonarCloud'// must match the name of an actual scanner installation directory on your Jenkins build agent
            }
            withSonarQubeEnv('SonarCloud') {
              sh "${scannerHome}/bin/sonar-scanner"
            }
          }
        }
    }
}