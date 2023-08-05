pipeline {
    agent any
    triggers { cron('* * * * *') }
    
    tools {
        maven 'maven-3.9.1'
        
        }
    stages {
        stage('git clone'){
            steps {
            
                git branch: 'main', url: 'https://github.com/hanumantharao19/docker-maven-image.git'
            }
        }
        
        stage('display jenkins url'){
            steps {
                echo "${JENKINS_URL}"
            }
        }
        
        stage('maven build'){
            steps {
                sh 'mvn clean install'
            }
        }
        
        stage('docker login'){
            steps {
                sh 'docker login -u hanumantharao1986 -p Haswitha@1986'
            }
            
        }
        
        stage('docker build') {
            steps {
                sh 'docker build -t hanumantharao1986/mahi_java:${BUILD_NUMBER} .' 
            }
        }
        
        stage('docker image push to docker registry') {
            steps {
                sh 'docker push hanumantharao1986/mahi_java:${BUILD_NUMBER}'
            }
        }
       
    }
}
