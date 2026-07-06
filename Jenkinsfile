@Library("Shared") _
pipeline {
    agent { label "vinod" }
    
    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
                script{
                    clone("https://github.com/akash9889Git/django-notes-app.git","main")
                }
            }
        }
        stage("Build") {
            steps {
                script{
                    docker_build("notes-app","v1","kubeakash9889")
                }
            }
        }
        stage("Push to DockerHub") {
            steps {
              script{
                  docker_push("notes-app","v1","kubeakash9889")
              }
                }
        }
        stage("Deploy") {
            steps {
                echo "This is Deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
