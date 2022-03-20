pipeline {
    agent any
    tools {maven 'maven-3.8'
    }
    stages {
        stage('build jar') {
            steps {
                echo "building app..."
                sh 'mvn package'
            }
        }
        stage('build image') {
            steps {
                echo 'building docker image..'
                withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerpwd')]) {
                sh 'docker build -t gwin8/jenkins-pipeline:jenks-img-1.0 .'
                sh "docker login -u gwin8 -p {$dockerpwd}"
                sh 'docker push gwin8/jenkins-pipeline:jenks-img-1.0'
                }
            }
        } 
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
