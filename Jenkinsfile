pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'pip3 install --break-system-packages --timeout 120 --retries 5 pyspark pytest'
            }
        }
        stage('Test') {
            steps {
                sh 'python3 -m pytest'
            }
        }
        stage('Package') {
            steps {
                sh 'zip -r retailproject.zip .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'mkdir -p /var/jenkins_home/deployed'
                sh 'cp retailproject.zip /var/jenkins_home/deployed/'
            }
        }
    }
}