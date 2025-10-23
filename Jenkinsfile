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