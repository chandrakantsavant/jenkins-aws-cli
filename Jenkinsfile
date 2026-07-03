pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'amazon/aws-cli'
                    args "--entrypoint=''"
                    reuseNode true
                }
            }
            steps {
                sh 'aws --version'
                sh 'aws s3 ls'
            }
        }
    }
}
