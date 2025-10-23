pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Source code checked out."
            }
        }
        
        // Use 'bat' instead of 'sh' for Windows agents
        stage('Build & Test') { 
            steps {                
                // CRITICAL CHANGE: using 'bat'
                bat 'mvn clean install'
            }
            post {
                always {
                    // This now reliably finds the reports generated in the steps block.
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
       
        stage('Run Application') {
            // CRITICAL CHANGE: using 'bat'
            steps {
                bat 'java -cp target/java-standalone-application-1.0-SNAPSHOT.jar com.expertszen.App'
            }
        }
    }
}