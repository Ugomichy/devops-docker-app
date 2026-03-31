pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
            }
        }

        stage('Test') {
            stage('Deploy') {
    steps {
        sh '''
        ssh -o StrictHostKeyChecking=no -i key.pem ubuntu@18.195.201.40 << 'EOF'
        cd devops-docker-app
        git pull
        docker-compose down
        docker-compose up -d --build
        EOF
        '''
    }
}
