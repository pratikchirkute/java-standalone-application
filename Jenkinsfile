pipeline {
    // CHANGE 'agent any' to 'agent { label 'master' }'
    agent { label 'master' } 

    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Source code checked out." // This MUST execute now
            }
        }
        
        stage('Build & Test') { 
            steps {                
                // Use 'bat' for Windows shell execution
                bat 'mvn clean install' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
       
        stage('Run Application') {
            steps {
                // Use 'bat' for Windows shell execution
                bat 'java -cp target/java-standalone-application-1.0-SNAPSHOT.jar com.expertszen.App'
            }
        }
    }
}