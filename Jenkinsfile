pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000 -p 5000:5000' 
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Push') {
            steps {
                docker.withRegistry('https://registry.example.com', 'credentials-id') {
                def customImage = docker.build("my-image:${env.BUILD_ID}")
                /* Push the container to the custom Registry */
                customImage.push()
            }
        }
    }
  }
}
