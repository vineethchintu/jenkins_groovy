pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub
                git url: 'https://github.com/vineethchintu/jenkins_groovy.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo "🚧 Starting Build..."
                sh './build.sh'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running Tests..."
                sh './test.sh'
            }
        }

        stage('Approval & Deploy') {
            steps {
                script {
                    timeout(time: 1, unit: 'HOURS') {
                        input message: "Deploy to Production?", ok: "Deploy"
                    }
                    echo "🚀 Deploying..."
                    sh './deploy.sh'
                }
            }
        }
    }

    post {
        always {
            echo "🔔 Always runs"
        }
        success {
            echo "✅ Pipeline succeeded"
        }
        failure {
            echo "❌ Pipeline failed"
        }
    }
}

