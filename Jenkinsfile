pipeline {
    agent any
    
    // TEMPORARILY REMOVE 'tools' TO TEST EXECUTION
    /*
    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }
    */

    stages {
        stage('Test Execution') {
            steps {
                // This MUST execute.
                bat 'echo Agent is running on the Built-In Node.' 
            }
        }
    }
}