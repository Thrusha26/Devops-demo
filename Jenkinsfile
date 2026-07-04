pipeline{
    agent any

    tools{
        jdk 'java-11'
        maven 'maven'
    }

    stages{
        stage ('git-checkout'){
            steps{
                git branch: 'dev', url: 'https://github.com/Thrusha26/Devops-demo.git'
            }
        }
        stage ('mvn clean'){
            steps{
                sh 'mvn clean'
            }
        }
        stage ('mvn packaging'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage ('Build and tag'){
            steps{
                sh 'docker buil -t trishaa98/project-1 .'
            }
        }
        stage ('Containerisation'){
            steps{
                sh '''
                docker run -it -d --name c8 -p 9008:8080 trishaa98/project-1
                '''
            }
        }
        stage ('Login to Docker Hub'){
            steps{
                script{
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh "echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin"
                    }
                }                  
            }
        }
        stage ('Pushing image to repository'){
            steps{
                sh 'docker push trishaa98/project-1'
            }
        }
    }
}
