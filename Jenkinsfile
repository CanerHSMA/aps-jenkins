pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')  // Überprüft alle 5 Minuten auf Änderungen
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'echo "Build completed"'  // Simuliert den Build-Schritt
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo "All tests passed!"'  // Simuliert den Test-Schritt
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                sh 'echo "Deployment complete!"'  // Simuliert einen einfachen Deploy-Schritt
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            cleanWs()
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
