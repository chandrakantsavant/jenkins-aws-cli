pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'amazon/aws-cli'
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
