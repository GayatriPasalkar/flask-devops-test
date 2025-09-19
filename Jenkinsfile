pipeline {
    agent any

    environment {
        // Ensure Java 21 is available everywhere in the pipeline
        JAVA_HOME = "/opt/java/openjdk"
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/GayatriPasalkar/flask-devops-test.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    rm -rf venv
                    python3 -m venv venv
                    ./venv/bin/pip install --upgrade pip
                    ./venv/bin/pip install --no-cache-dir -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    ./venv/bin/pytest --cov=. --cov-report=xml test_app.py
                '''
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('MySonarQubeServer') {
                    sh '''
                        echo "Using Java from: $JAVA_HOME"
                        which java
                        java -version
                        sonar-scanner
                    '''
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline execution completed."
        }
    }
}
