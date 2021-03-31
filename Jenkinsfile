pipeline {
    agent any
    
    stages{
        stage("CheckOut") {
            steps{
             checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/maan98/my-app.git']]])
            }
        }
         stage('Test') {
            steps {
                sh 'mvn --version'
            }
        }
        stage("Maven Build") {
            steps {
                sh 'mvn clean install -f my-app/pom.xml'
            }
        }
    }
}
