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
                sh 'mvn clean package -DskipTests' 
            }
        }
        
        stage('Run Application') {
            steps {
                sh 'java -jar target/java-standalone-application-1.0-SNAPSHOT.jar &' 
                
                sh 'sleep 5' 
				
                echo "Application started in background."
            }
        }
        
        stage('Test') {
            steps {
                // Run the tests
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                    
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                }
            }
        }
    }
}