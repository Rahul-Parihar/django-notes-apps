@Library("Shared") _
pipeline {
    agent { label "Vinod" }

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
                git branch: 'main', url: 'https://github.com/Rahul-Parihar/django-notes-apps.git'
                }
            }
        }

        stage("Build") {
            steps {
                script{
                docker_build("notes-app","latest", "rahulsinghparihar")
                }
            }
        }

        stage("Push to DockerHub") {
            steps {
                script{
                    docker_push("notes-app","latest","rahulsinghparihar")
                
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "Deploying the Docker container..."
                sh "docker compose down || true"
                sh "docker compose up -d"
            }
        }
    }
}
