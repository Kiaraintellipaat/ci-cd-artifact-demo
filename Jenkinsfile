pipeline {
    agent any

    tools {
        jdk 'Java11'
        maven 'Maven'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Kiaraintellipaat/ci-cd-artifact-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Artifact created and archived successfully'
        }
        failure {
            echo 'Build failed'
        }
    }
}
