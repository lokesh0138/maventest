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
        }
     
        stage('Package') {
            steps {
                echo 'mvn install'
            }
            post {
                success{
                    bat 'echo "Packaging done"'
                }
                failure{
                    bat 'echo "Packaging failure"'
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
            }
        }
     

      
          
        
        
    }
}
