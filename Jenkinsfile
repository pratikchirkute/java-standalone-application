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
                sh 'mvn clean install'
            }
        }
        
        stage('Run Application') {
            steps {
                sh 'java -cp target/java-standalone-application-1.0-SNAPSHOT.jar com.expertszen.App'
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
                }
            }
        }
    }
}