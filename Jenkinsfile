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
        
        // **REPLACE** the old 'Build' and 'Test' stages with this:
        stage('Build & Test') { 
            steps {                
                // This command runs the compilation, tests, and packaging.
                sh 'mvn clean install'
            }
            post {
                always {
                    // Publish reports immediately after they are generated.
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