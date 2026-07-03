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
            environment {
                AWS_S3_BUCKET = 'chand-tf-bucket'
            }
            steps {
                withCredentials([usernamePassword(credentialsId: 'aws-cred', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {
                    sh '''
                    aws --version
                    aws s3 ls
                    echo "Hello S3 This is Chandrakant..." > index.html
                    aws s3 cp index.html s3://$AWS_S3_BUCKET/index.html
                    '''
                }
               
            }
        }
    }
}
