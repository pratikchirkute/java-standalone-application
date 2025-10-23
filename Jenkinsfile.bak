pipeline {
    agent any

    // Ensure 'JDK17' and 'Maven3' are configured in Manage Jenkins > Global Tool Configuration
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
        
        stage('Build') {
            steps {
                // Changed 'sh' to 'bat' for Windows environment
                bat 'mvn clean install' 
            }
        }
      
        stage('Run Application') {
            steps {
                // Changed 'sh' to 'bat' for Windows environment
                // To run the app in the background on Windows, use 'start /B'
                // Or, better for a Jenkins pipeline, run it normally and end the step
                bat 'java -jar target/java-standalone-application-1.0-SNAPSHOT.jar' 
                
                // You may not need a sleep command here unless a subsequent step relies on the app running
                // bat 'timeout /t 5' 
				
                echo "Application started (or step executed)."
            }
        }
        
        stage('Test') {
            steps {
                // Run the tests
                // Changed 'sh' to 'bat' for Windows environment
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