pipeline {
    agent any

    tools {
        maven 'mvn'   // Make sure this name matches your Jenkins tool config
    }

    environment {
        GIT_REPO = 'https://github.com/RaviMargaveni-hub/spring3-mvc-maven-xml-hello-world-1.git'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: "${GIT_REPO}"
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully.'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
