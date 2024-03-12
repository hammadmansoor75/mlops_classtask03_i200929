pipeline {
    agent any
    
    stages {
        stage('Cloning repository') {
            steps {
                git 'https://github.com/hammadmansoor75/mlops_classtask03_i200929.git'
            }
        }
        
        stage('Installation of dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Execution of test.py') {
            steps {
                sh 'python test.py'
            }
        }
        
        stage('Deploying step') {
            steps {
                script {
                    def branchName = sh(script: 'git rev-parse --abbrev-ref HEAD', returnStdout: true).trim()
                    if (branchName == 'main') {
                        echo 'Deploying to production'
                        
                    } else {
                        echo 'Deploying to UAT'
                       
                    }
                }
            }
        }
    }
}
