pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh "java --version"
            }
        }
        stage('Test') {
            steps {
                sh "java --version"
            }
        }
        stage('Release') {
            steps {
              withCredentials([usernamePassword(credentialsId: 'dockerhubcredentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                sh '''
                docker login -u $USERNAME -p $PASSWORD
                docker build -t shumimalik/backendjenkins:${BUILD_NUMBER} .
                docker push shumimalik/backendjenkins:${BUILD_NUMBER}
                '''
                
              }
            }
        }
    }
}
