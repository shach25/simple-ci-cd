pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker Image...'
                sh 'docker build -t simple-web-app .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Docker Container...'
                // Run container temporarily for test
                sh '''
                docker run -d --name temp-web-app -p 8082:80 simple-web-app
                sleep 5
                if docker ps | grep -q temp-web-app; then
                    echo "Test Passed: Container is running"
                else
                    echo "Test Failed: Container not running"
                    exit 1
                fi
                docker stop temp-web-app
                docker rm temp-web-app
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application...'
                sh '''
                docker ps -q --filter "name=final-web-app" | grep -q . && docker stop final-web-app && docker rm final-web-app || true
                docker run -d -p 8081:80 --name final-web-app simple-web-app
                '''
            }
        }
    }
}


