@Library("shared") _
pipeline{
    
    agent { label "Server1" }

    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("Code"){
            steps{
               script{
                clone("https://github.com/Rahul-Parihar/django-notes-apps.git", "main")
               }
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","rahulsinghparihar")
                }
            }
        }
        stage("Push to Dockerhub"){
            steps{
               script{
                   docker_push("notes-app","latest","rahulsinghparihar")
               }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
