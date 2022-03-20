pipeline {
    agent any
    tools {maven 'maven-3.8'
    }
    stages {
        stage('build jar') {
            steps {
                echo "building app..."
                sh 'mvn clean package'
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
>>>>>>> 9bd75bf0ef26f2e9cc8969dcdebd51a1f5b02b7c
