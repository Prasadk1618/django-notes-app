@Library("Shared") _
pipeline{
    
    agent { label "Prasad" }
    
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
                echo "This Is Cloning The Code..!!"
                git url: "https://github.com/Prasadk1618/django-notes-app.git", branch:"main"
                echo "Code Clone Successfully..!!"
            }
        }
        stage("Build"){
            steps{
                echo "This Is Building The Code..!!"
                sh "whoami"
                sh "docker build -t notes-app:latest ."
            }
        }
        stage("Push To DockerHub"){
            steps{
              script{
                  docker_push("notes-app","latest","devopsbabu16")
              }
            }
        }
        stage("Deploy"){
            steps{
                echo "This Is Deploying The Code..!!"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
