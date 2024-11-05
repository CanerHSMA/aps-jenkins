pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')   // Überprüft alle 5 Minuten auf Änderungen im Repository
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                script {
                    if (fileExists('hello.sh')) {
                        echo 'hello.sh file found. Proceeding with the build...'
                        sh 'chmod +x hello.sh'  // Macht das Skript ausführbar, falls notwendig
                        sh './hello.sh'  // Führt das hello.sh-Skript aus
                    } else {
                        echo 'hello.sh file not found. Skipping the build.'
                    }
                }
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
