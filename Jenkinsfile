pipeline {
    agent {
        label "slave-1"
    }
    
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
                checkout scm
            }
        }
        stage('Debug'){
            steps {
                sh "ls -lha"
            }
        }
        stage('Start app'){
            steps {
                sh "docker compose down"
                sh "docker compose up --build -d"
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
