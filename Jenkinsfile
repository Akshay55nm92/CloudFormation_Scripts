pipeline {
    agent any
    stages {
        stage('Creating empty S3 Bucket and SQS') {
            steps {
                echo "Executing CF script to create S3 bucket";
                sh 'aws cloudformation create-stack --stack-name jenkiscft-s3 --template-body file://s3samp2.json'
                echo "Executing CF script to create sqs";
                sh 'aws cloudformation create-stack --stack-name jenkiscft-sqs --template-body file://sqssamp.json'
            }
        }
    }

    post { 
        success {
            echo "Success"
        }
        failure {
            echo "Failed"
        }
        unstable {
            echo "Unstable"
        }
        changed {
            echo "State of the pipeline has changed"
        }
    }
}
