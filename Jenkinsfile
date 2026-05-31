pipeline {
    agent any
    stages {
        stage('Step 1: Check out code from GitHub') {
            steps {
                // Jenkins will now pull from your master branch online
                git branch: 'master', url: 'https://github.com/ali802/jenkins-mini-project.git'
                echo 'Code successfully pulled from GitHub!'
            }
        }
        stage('Step 2: Build Docker block') {
            steps {
                sh 'docker build -t my-website .'
            }
        }
        stage('Step 3: Deploy the Container') {
            steps {
                sh 'docker rm -f live-webserver || true'
                sh 'docker run -d --name live-webserver -p 80:80 my-website'
                echo 'Application is live!'
            }
        }
    }
}
