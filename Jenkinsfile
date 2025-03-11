pipeline {
    agent any

    stages {
        stage('Pre-Build Checks') {
            steps {
                script {
                    echo "Running Pre-Build Checks..."

                    // Run linting
                    sh 'eslint src/ || exit 1'
                    sh 'pylint my_python_script.py || exit 1'

                    // Run security scans
                    sh 'trufflehog --regex --entropy=False . || exit 1'

                    // Run unit tests with coverage
                    sh 'pytest --cov=my_project || exit 1'
                }
            }
        }

        stage('Build') {
            steps {
                echo "Building the Project..."
                sh 'mvn clean package'
            }
        }

        stage('Post-Build') {
            steps {
                echo "Build Completed Successfully!"
            }
        }
    }
}
