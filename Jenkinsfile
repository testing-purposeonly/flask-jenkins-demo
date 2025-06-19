pipeline {
    agent any

    environment {
        PATH = "/var/lib/jenkins/.local/bin:$PATH"
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
                sh 'pip3 install --user bandit'
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

