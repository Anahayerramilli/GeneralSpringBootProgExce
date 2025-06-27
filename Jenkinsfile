pipeline {
    agent any

    environment {
        // This picks the SonarQube token stored in Jenkins credentials (ID = sonar-token)
        SONAR_TOKEN = credentials('sonar-token')
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'development', url: 'https://github.com/Anahayerramilli/GeneralSpringBootProgExce.git'
            }
        }

        stage('Build and SonarQube Analysis') {
            steps {
                withSonarQubeEnv('LocalSonarQube') {
                    sh """
                        mvn clean verify sonar:sonar \
                        -Dsonar.projectKey=GeneralSpringBootProgExce \
                        -Dsonar.token=$SONAR_TOKEN
                    """
                }
            }
        }
    }
}
