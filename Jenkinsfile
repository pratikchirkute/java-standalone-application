pipeline {
    agent any
    
    // COMMENT OUT the entire tools block
    // tools {
    //     jdk 'JDK17'
    //     maven 'Maven3'
    // }

    stages {
        stage('Test Execution') {
            steps {
                // This MUST execute if the agent is available.
                bat 'echo Agent is running on the Built-In Node.'
            }
        }
    }
}