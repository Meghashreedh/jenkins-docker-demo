pipeline {
    agent any

    environment {
        IMAGE_NAME = "jenkins-demo"
        IMAGE_TAG = "v1"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
            }
        }

       stage('Run Container') {
            steps {
                sh '''
        docker rm -f demo || true
        docker rm -f jenkins-demo || true
        docker run -d -p 8081:80 --name demo $IMAGE_NAME:$IMAGE_TAG
        '''
    }
}
        }
    }
}

