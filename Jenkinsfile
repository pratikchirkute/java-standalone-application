pipeline {
    agent any

    // Ensure 'JDK17' and 'Maven3' are configured in Global Tool Configuration
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
        
        stage('Build & Test') { 
            steps {                
                // Use 'bat' for Windows shell execution
                bat 'mvn clean install' 
            }
            post {
                // The 'always' block ensures this runs whether mvn succeeds or fails
                always {
                    // This is the CORRECT location for the JUnit publisher (inside the script)
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