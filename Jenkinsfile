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
                sh '''
                ssh -o StrictHostKeyChecking=no ubuntu@18.185.60.7 << EOF

                cd ~

                if [ ! -d "devops-docker-app" ]; then
                    git clone https://github.com/ugomichy/devops-docker-app.git
                fi

                cd devops-docker-app
                git pull

                docker compose down
                docker compose up -d --build

                EOF
                '''
            }
        }
    }
}
