@Library("shared") _
pipeline {
    agent { label "vinod"}

    stages {
        stage('Hello'){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code'){
            steps {
                script {
                    echo 'This is cloning the code'
                    clone("https://github.com/GauravJ1128/notes-app.git","main")
                }
            }
        }
         stage('Build'){
            steps {
                script{
                    docker_build("notes-app","latest","gauravjain6928")
                }
            }
        }
        stage('Test'){
            steps {
                echo 'This is testing the code'
            }
        }
        stage('Push image to docker hub'){
            steps{
                script{
                    echo 'Pushing image to docker hub'
                    docker_push("notes-app","latest","gauravjain6928")
                }
            }
        }
         stage('Deploy'){
            steps {
                echo 'This is deploying the code'
                sh 'docker compose down  && docker compose up -d'
            }
        }
    }
}
