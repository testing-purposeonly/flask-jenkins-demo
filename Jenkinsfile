pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/testing-purposeonly/flask-jenkins-demo'
            }
        }
        stage('Install Requirements') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Run App') {
            steps {
                sh 'nohup python app.py &'
            }
        }
    }
}

