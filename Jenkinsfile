pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kyongseo/apidemo.git', credentialsId: 'ks_github_id'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'chmod 755 ./gradlew'
                sh './gradlew build'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // test steps
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                 withAWS(credentials: 'lion_user') {
                                    sh 'aws s3 cp build/libs/apidemo-0.0.1-SNAPSHOT.jar s3://ks-build-files/'
                                }
            }
        }
    }
}