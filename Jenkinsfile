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
         stage('Test sonar code quality') {
            steps {
                no public field ‘webhookSecretId’ (or getter method) found in class org.sonarsource.scanner.jenkins.pipeline.WaitForQualityGateStep
                sh 'mvn sonar:sonar'
            }
        }
        stage("Maven Build") {
            steps {
                sh 'mvn clean install -f my-app/pom.xml'
            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
               echo "successfully depoyed"
            }
        }
    }
}
