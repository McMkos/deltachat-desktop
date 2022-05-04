pipeline {
    agent any

    stages {
        
        stage('Build') {
            steps {
                echo 'Building has started'
                sh 'docker-compose build build-agent'
            }
            
            post {
            	 success {
            	 	echo 'Building succeded!'
            	 }
            	 
            	 failure {
            	 	echo 'Building failed!'
            	 }
            }
        }
        
        stage('Test') {
            steps {
            	 echo 'Testing has started'
                sh 'docker-compose build test-agent'
                sh 'docker-compose up -d test-agent'
            }
            
             post {
            	 success {
            	 	echo 'Testing succeded!'
            	 }
            	 
            	 failure {
            	 	echo 'Testing failed!'
            	 }
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying has started'
                echo 'Blagam unizenie zadzialaj'
            }
            
             post {
            	 success {
            	 	echo 'Deploying succeded!'
            	 }
            	 
            	 failure {
            	 	echo 'Deploying failed!'
            	 }
            }
        }
    }
}
