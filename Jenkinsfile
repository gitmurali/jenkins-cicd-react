pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
                sh 'ls'
                sh 'cd build'
                sh 'ls'
            }
        }
        stage('S3 Upload') {
            steps {
                withAWS(region: 'us-east-1', credentials: '90516043-3031-4352-89ae-cba8fc8194b9') {
                    sh 'ls -la build'
                    sh 'aws s3 cp build s3://jenkins-react-sk/ --recursive'
                }
            }
        }
    }
}
