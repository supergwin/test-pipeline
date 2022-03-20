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
                withCredentials([usernameColonPassword(credentialsId: 'dockerhub-creds', variable: 'dockerhub')]) {
                    sh 'docker build -t gwin8/jenkins-pipeline:jenks-img-1.0 .'
                    sh "docker login -u $dockerhub -p $dockerhub"
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
<<<<<<< HEAD
}
=======
}
>>>>>>> 8657f46a8bf5198c0064b0b720398751943b8027
