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
        
        stage('Build & Test') { // Combine stages
            steps {                
                // This command runs the compilation, tests, and packaging.
                sh 'mvn clean install'
            }
            post {
                always {
                    // Publish reports immediately after the command that creates them.
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
       
        stage('Run Application') {
            steps {
                sh 'java -cp target/java-standalone-application-1.0-SNAPSHOT.jar com.expertszen.App'
            }
        }
    }
}