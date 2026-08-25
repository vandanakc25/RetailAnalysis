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
                sh 'tar --exclude=retailproject.tar.gz -czf retailproject.tar.gz .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'mkdir -p /var/jenkins_home/deployed'
                sh 'cp retailproject.tar.gz /var/jenkins_home/deployed/'
                sh 'ls -la /var/jenkins_home/deployed/'
            }
        }
    }
}