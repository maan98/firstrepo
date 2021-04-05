pipeline {
    agent any
    
    stages{
        stage("CheckOut") {
            steps{
             checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/maan98/firstrepo.git']]])
            }
        }
         stage('Test') {
            steps {
                sh 'mvn --version'
            }
        }
        stage("Maven Build") {
            steps {
                sh 'mvn clean'
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
