pipeline {
    agent any


    stages {
        stage('Clone') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/ninotahrbx/Brick-Game-9999-in-1.git'

            }

        }

        stage('Test') {
            steps {
                // Get some code from a GitHub repository
                bat "mvn test"

            }

        }

        stage('Package') {
            steps {
                // Get some code from a GitHub repository
                bat "mvn clean package -DskipTests"

            }
            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    archiveArtifacts 'target/*.jar'
                }
            }

        }

    }
}
