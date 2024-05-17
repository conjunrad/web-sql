pipeline {
    agent any
    
    environment {
        REPO_URL = "git@github.com:conjunrad/web-sql.git"
    }
    
    stages {
        stage('Setup known hosts'){
            steps {
                sh 'ssh-keyscan github.com >> ~/.ssh/known_hosts'
            }
        }
        stage('Clone repo'){
            steps {
                sh "git clone ${REPO_URL}"
            }
        }
        stage('Debug'){
            steps {
                sh "ls -lha"
            }
        }
        stage('Start app'){
            steps {
                sh "cd web-sql"
                sh "docker compose up -d"
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
