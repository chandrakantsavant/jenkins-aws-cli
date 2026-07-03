pipeline {
    agent any
    environment {
        AWS_REGION = 'us-east-1'
    }
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
                withCredentials([usernamePassword(credentialsId: 'aws-cred', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {
                    sh '''
                    aws --version
                    aws s3 ls
                    echo "Hello S3 This is Chandrakant..." > index.html
                    aws s3 cp index.html s3://chand-tf-bucket/index.html
                    '''
                }
               
            }
        }
    }
}
