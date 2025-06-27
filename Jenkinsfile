pipeline {
    agent any

    environment {
        SONAR_TOKEN = credentials('sonar-token')
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Anahayerramilli/GeneralSpringBootProgExce.git', branch: 'development'
            }
        }

        stage('Build & Analyze') {
            steps {
                withSonarQubeEnv('LocalSonarQube') {
                    sh """
                        mvn clean verify sonar:sonar \
                        -Dsonar.projectKey=GeneralSpringBootProgExce \
                        -Dsonar.login=$SONAR_TOKEN
                    """
                }
            }
        }
    }
}
