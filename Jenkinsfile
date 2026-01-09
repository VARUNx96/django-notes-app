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
                echo "dowing all prev containes..."
                sh "docker compose down"
                script{
                    deploy()
                }
            }
        }
    }
}
