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
                git branch: "${params.BRANCH}", url: 'https://github.com/vineethchintu/jenkins_groovy.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh './build.sh'
                    } else {
                        bat 'build.bat'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    if (isUnix()) {
                        sh './test.sh'
                    } else {
                        bat 'test.bat'
                    }
                }
            }
        }

        stage('Approval') {
            when {
                expression { params.DEPLOY }
            }
            steps {
                input message: "Deploy to ${APP_ENV}?", ok: "Deploy Now"
            }
        }

        stage('Deploy') {
            when {
                expression { params.DEPLOY }
            }
            steps {
                echo "Deploying version ${VERSION} to ${APP_ENV}"
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
            echo "🔔 Always runs"
        }
    }
}


