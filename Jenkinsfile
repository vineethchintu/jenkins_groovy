pipeline {
    agent any
    
    environment {
        APP_ENV = "staging"
        VERSION = "1.0.${BUILD_NUMBER}"
    }

    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Branch to build')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Deploy after build?')
    }

    stages {
        stage('Clone') {
            steps {
<<<<<<< HEAD
=======
                echo "📥 Cloning branch: ${params.BRANCH}"
>>>>>>> 53ac58f (Normalize line endings to LF)
                git branch: "${params.BRANCH}", url: 'https://github.com/vineethchintu/jenkins_groovy.git'
            }
        }

        stage('Build') {
            steps {
<<<<<<< HEAD
                script {
                    if (isUnix()) {
                        sh './build.sh'
                    } else {
                        bat 'build.bat'
                    }
                }
=======
                echo "🔨 Starting Build..."
                sh 'chmod +x build.sh'
                sh './build.sh'
>>>>>>> 53ac58f (Normalize line endings to LF)
            }
        }

        stage('Test') {
            steps {
<<<<<<< HEAD
                script {
                    if (isUnix()) {
                        sh './test.sh'
                    } else {
                        bat 'test.bat'
                    }
                }
=======
                echo "🧪 Running Tests..."
                sh 'chmod +x test.sh'
                sh './test.sh'
>>>>>>> 53ac58f (Normalize line endings to LF)
            }
        }

        stage('Approval') {
            when {
                expression { params.DEPLOY }
            }
            steps {
<<<<<<< HEAD
                input message: "Deploy to ${APP_ENV}?", ok: "Deploy Now"
=======
                input message: "🚦 Do you want to deploy to ${APP_ENV}?", ok: "Deploy Now"
>>>>>>> 53ac58f (Normalize line endings to LF)
            }
        }

        stage('Deploy') {
            when {
                expression { params.DEPLOY }
            }
            steps {
<<<<<<< HEAD
                echo "Deploying version ${VERSION} to ${APP_ENV}"
=======
                echo "🚀 Deploying version ${VERSION} to ${APP_ENV}..."
                sh 'chmod +x deploy.sh'
                sh './deploy.sh'
>>>>>>> 53ac58f (Normalize line endings to LF)
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline finished successfully"
        }
        failure {
            echo "❌ Pipeline failed"
        }
        always {
<<<<<<< HEAD
            echo "🔔 Always runs"
        }
    }
}


=======
            echo "🔔 Cleanup or notifications can go here"
        }
    }
}
>>>>>>> 53ac58f (Normalize line endings to LF)
