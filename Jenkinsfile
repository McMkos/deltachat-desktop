pipeline {
    agent any

    stages {
        
        stage('Test') {
            steps {
                sh 'docker build -t test-agent'
                sh 'docker run -it test-agent'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building'
            }
        }
        
    }
}
