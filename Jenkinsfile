pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'pip3 install --user pipenv --break-system-packages'
                sh 'python3 -m pipenv --rm || exit 0'
                sh 'python3 -m pipenv install'
            }
        }
        stage('Test') {
            steps {
                sh 'python3 -m pipenv run pytest'
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