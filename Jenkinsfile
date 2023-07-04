
pipeline {
  agent any
  
  environment {
    function_name = 'aws-1-pepiline'
  }
  
  stages {
    stage('Build') {
      steps {
        // Build the Java project using Maven
        sh 'mvn clean package'
      }
    }
    
    stage('Push to S3') {
      steps {
        // Push the built JAR file to an S3 bucket
        sh 'aws s3 cp target/java-test-1.jar s3://redbull-f1/'
      }
    }
    
    stage('Deploy to Lambda') {
      steps {
        // Deploy the JAR file to AWS Lambda
        sh 'aws lambda update-function-code --function-name aws-1-pepiline --s3-bucket redbull-f1 --s3-key java-test-1.jar'
      }
    }
  }
}

