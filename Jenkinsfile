pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/RohiniJ1204/flask-cicd-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest'
            }
        }

        stage('Run App') {
            steps {
                sh 'nohup python app.py &'
            }
        }
    }
}
