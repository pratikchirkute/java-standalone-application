pipeline {
    agent any


    stages {
        stage('Checkout') {
            steps {
                // This line will now execute after the tool path is fixed
                echo "Source code checked out."
            }
        }
        
        // COMBINED STAGE to fix the 'No test report files found' error
        stage('Build & Test') { 
            steps {                
                // CRITICAL FIX for Windows agent: Use 'bat' instead of 'sh'
                bat 'mvn clean install' 
            }
            post {
                always {
                    // Publish reports immediately after they are generated
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
       
        stage('Run Application') {
            steps {
                // CRITICAL FIX for Windows agent: Use 'bat' instead of 'sh'
                bat 'java -cp target/java-standalone-application-1.0-SNAPSHOT.jar com.expertszen.App'
            }
        }
    }
}