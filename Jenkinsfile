pipeline {
    agent any

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
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER' passwordVariable: 'PASS')]
                    sh 'docker build -t gwin8/jenkins-pipeline:jenks-img-1.0 .'
                    sh "echo $PASS | docker login -u $USER --pasword-stdin"
                    sh 'docker push gwin8/jenkins-pipeline:jenks-img-1.0'
            }
        } 
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}

