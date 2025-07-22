pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'git@github.com:srthesmarty/flask-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Restart Flask App') {
            steps {
                sh 'pm2 delete flask || true'
                sh 'pm2 start app.py --name flask'
            }
        }
    }
}
