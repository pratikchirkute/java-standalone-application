pipeline {
    agent any
    
    // KEEP THIS REMOVED until the pipeline runs successfully
    /*
    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }
    */

    stages {
        stage('Checkout') {
            steps {
                echo "Source code checked out." 
            }
        }
        
        stage('Build & Test') { 
            steps {                
                // This command will fail because Maven isn't on the PATH, but it should START
                bat 'mvn clean install' 
            }
            post {
                always {
                    // Temporarily exclude JUnit to prevent failure if mvn fails to create reports
                    // junit 'target/surefire-reports/*.xml' 
                }
            }
        }
       
        stage('Run Application') {
            steps {
                // This command will also fail, but the stage should START
                bat 'java -cp target/java-standalone-application-1.0-SNAPSHOT.jar com.expertszen.App'
            }
        }
    }
}