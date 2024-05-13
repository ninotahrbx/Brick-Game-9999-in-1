pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                // git 'https://github.com/ninotahrbx/Brick-Game-9999-in-1.git'
                sh "mvn compile"
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('Mon-SonarQube') {
                    sh 'sonar-scanner'
                }
        }      
        // stage('Test') {
        //     steps {
        //         sh "mvn test" // Cela exécutera les tests Maven
        //     }
        // }
        stage('Package') {
            steps {
                sh "mvn clean package -DskipTests=true" // Cela empaquètera le projet en sautant les tests
            }
            post {
                success {
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
