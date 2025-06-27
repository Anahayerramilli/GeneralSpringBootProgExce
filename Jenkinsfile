pipeline {
    agent any

    tools {
        maven 'Maven3'           // Use the name you configured under Global Tool Config
        jdk 'JDK17'              // Optional: Only if you installed a JDK via Jenkins tools
    }

    environment {
        SONAR_TOKEN = credentials('sonar-token')  // Uses the secret token from Jenkins credentials
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
