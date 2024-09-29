@Library("Shared") _
pipeline{
    agent {label "vinod"}
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
                    clone("https://github.com/LondheShubham153/django-notes-app.git","main") 
               }
            }
        }
        stage("Build"){
            steps{
               script{
                 docker_build("notes-app","latest","amish28")
               }
            }
        }
        stage("Push to Docker Hub"){
            steps{
               script{
                   docker_push("notes-app","latest","amish28")
               
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh "docker compose up -d"
            }    
        }
    }
}
