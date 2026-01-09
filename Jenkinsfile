@Library("shared") _
pipeline {
    agent any
    stages{
        stage('hello'){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code'){
            steps{
                script{
                    clone("https://github.com/LondheShubham153/django-notes-app.git","main")
                }
            }
        }
        stage('Build'){
            steps{
                script{
                    build("notes-app:latest")
                }
            } 
        }
        stage('pushing'){
            steps{
                script{
                    push("notes-app:latest")
                }
            }
        }
        stage('deploy'){
            steps{
                echo "downing all prev containes..."
                sh '''
                export PATH=/usr/local/bin:/opt/homebrew/bin:$PATH
                echo "PATH is: $PATH"
                docker compose down
                '''
                echo "all services are down...."
                ehco "now re deploying again to all services up...."
                script{
                    deploy()
                }
            }
        }
    }
}
