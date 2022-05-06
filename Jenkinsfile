pipeline {
    agent any
    
    environment {     
    DOCKERHUB_CREDENTIALS = credentials('mcmkos-dockerhub')     
} 

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
                echo 'Loging into Docker Hub'
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'docker tag build-agent:latest mcmkos/deltachat-desktop:latest'
                sh 'docker push mcmkos/deltachat-desktop:latest'
            }
            
             post {
            	 success {
            	 	echo 'Deploying succeded!'
            	 }
            	 
            	 failure {
            	 	echo 'Deploying failed!'
            	 }
            	 
            	 always {
            	 	echo 'Loging out Docker Hub'
            	 	sh 'docker logout'
            	 }
            }
        }
    }
}
