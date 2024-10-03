@Library('shared') _
pipeline{
    agent { label 'rohit' }
    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            
            steps{
                script{
                    clone("https://github.com/DeoreRohit4/django-notes-app.git", "main")
                }
            }
            
        }
        stage("Build"){
            
            steps{
                script{
                    docker_build("rohitd4","notes-app","latest")
                }
                
            }
        }
        stage("Push To DockerHub"){
            
            steps{
                script{
                    docker_push("notes-app","latest","rohitd4")
                }
                //echo "Pushing image to docker hub"
                //withCredentials([usernamePassword('credentialsId':"dockerhubcred",passwordVariable:"HUBPASS",usernameVariable:"USERNAME")]){
                //sh "docker login -u ${env.USERNAME} -p ${env.HUBPASS}"
                //sh "docker image tag  notes-app:latest ${env.USERNAME}/notes-app:latest"
                //sh "docker push ${env.USERNAME}/notes-app:latest"
                //}
            }
            
        }
        stage("Deploy"){
            
            steps{
              script{
                  docker_compose()
                  // last stage
                }
            }
            
        }
    }
}
