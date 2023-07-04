pipeline {
    agent any

    environment {
        function_name = 'java-simple'
    }

stage('Build') {
      steps {
        // Build the Java project using Maven
        sh 'mvn clean package'
      }
    }
    
    stage('Test') {
      steps {
        // Execute unit tests
        echo 'Test'
        sh 'mvn test'
      }
    }

        stage('Push') {
            steps {
                echo 'Push'

                sh "aws s3 cp target/sample-1.0.3.jar s3://redbull-f1"
            }
        }

        stage('Deploy') {
            steps {
                echo 'Build'
                sh "aws lambda update-function-code --function-name $function_name --region us-east-1 --s3-bucket redbull-f1 --s3-key sample-1.0.3.jar"
            }
        }
    }
}
