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
                // Run Bandit and *don't fail yet*
                sh 'bandit -r . --severity-level medium -f txt -o bandit-report.txt || true'

                // Show results in console
                sh 'cat bandit-report.txt'

                // Fail build manually if Bandit found issues
                sh '''
                    if grep -q "Issue:" bandit-report.txt; then
                        echo "Bandit found issues. Failing the build."
                        exit 1
                    fi
                '''
            }
        }
    }
}

