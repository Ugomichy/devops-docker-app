pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application...'
            }
        }

      stage('Deploy') {
    steps {
        sh """
ssh -o StrictHostKeyChecking=no -i /var/lib/jenkins/workspace/devops-docker-pipeline/key.pem ubuntu@18.195.201.40 << EOF
cd devops-docker-app
git pull
docker-compose down
docker-compose up -d --build
EOF
"""
    }
}
