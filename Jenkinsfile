 pipeline {
  tools {
    maven 'Maven3.8.3'
  }
    agent any
    stages {
        stage('Clean') {
            steps {
                echo 'Cleaning..'
                bat 'mvn -B -DskipTests clean'
            }
            post {
                success{
                   slackSend color: '#BADA55', message: 'clean successful!!'
                }
                failure{
                   slackSend color: '#BADA55', message: 'clean failed!!'
                }
            }
         
        }
     
        stage('Package') {
            steps {
                echo 'mvn install'
            }
              post {
                success{
                   slackSend color: '#BADA55', message: 'package successful!!'
                }
                failure{
                   slackSend color: '#BADA55', message: 'package failed!!'
                }
            }
         
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                bat 'mvn test'
            }
             post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
                 success{
                   slackSend color: '#BADA55', message: 'Test successful!!'
                }
                failure{
                   slackSend color: '#BADA55', message: 'Test failed!!'
                }
            }
        }
     

      
          
        
        
    }
}
