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

        // stage('Terraform Initialization'){
        //     steps{
        //         dir('Infra'){
        //             sh "terraform init"
        //         }
        //     }
        // }

        stage('SonarQube analysis') {
          steps {
            script {
                scannerHome = tool 'SonarCloud'// must match the name of an actual scanner installation directory on your Jenkins build agent
            }
            withSonarQubeEnv('SonarCloud') {
              sh "${scannerHome}/bin/sonar-scanner "+
                 "-Dsonar.organization=maazpatel-git "+
                 "-Dsonar.projectKey=maazpatel-git_jenkins-terraform "+
                 "-Dsonar.sources=. "+
                 "-Dsonar.host.url=https://sonarcloud.io"
            //   sh '''
            //     ${scannerHome}/bin/sonar-scanner \
            //      -Dsonar.organization=maazpatel-git \
            //      -Dsonar.projectKey=maazpatel-git_jenkins-terraform \
            //      -Dsonar.sources=. \
            //      -Dsonar.host.url=https://sonarcloud.io
            //   '''
            }
          }
        }
    }
}