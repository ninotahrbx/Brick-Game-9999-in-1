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
                sh "mvn -Dskiptest=true sonar:sonar -Dsonar.projectKey=projet-brick -Dsonar.projectName='projet-brick' -Dsonar.host.url='http://localhost:9000' -Dsonar.token=sqp_71778798eaa3e8715a3f6a7770644256dd779169"
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
