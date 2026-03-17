pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-cicd-app"
        CONTAINER_NAME = "flask-container"
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/RohiniJ1204/flask-cicd-project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh 'venv/bin/pip install -r app/requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'venv/bin/pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker stop $CONTAINER_NAME || true'
                sh 'docker rm $CONTAINER_NAME || true'
                sh 'docker run -d -p 6001:6000 --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }
    }
}
