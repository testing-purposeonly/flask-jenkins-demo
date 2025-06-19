pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
                sh 'pip3 install bandit'
            }
        }

        stage('SAST - Bandit Scan') {
            steps {
                sh 'bandit -r . --severity-level medium -f txt -o bandit-report.txt || exit 1'
                sh 'cat bandit-report.txt'
            }
        }
    }
}

