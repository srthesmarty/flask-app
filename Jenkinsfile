pipeline {
    agent any

    environment {
        VENV_PATH = './venv'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'git@github.com:srthesmarty/flask-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m venv ${VENV_PATH}
                    . ${VENV_PATH}/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Restart Flask App') {
            steps {
                sh '''
                    . ${VENV_PATH}/bin/activate
                    pm2 delete flask || true
                    pm2 start app.py --name flask
                '''
            }
        }
    }
}
