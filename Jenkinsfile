@Library("shared-libs") _
pipeline {
    agent {
        label 'agent-n1'
    }
    
    stages {
        stage('Checkout') {
            steps {
                script {
                      checkOut("https://github.com/mashoodkhan/django-notes-app.git","main")
                }
            }
        }
        stage('Build'){
            steps{
                script{
                    dockerbuild("mashoodk","notes-app","latest")
                }
              
            }
        }
    
        stage('Push to docker hub'){
            steps{
                echo 'Pushing image to docker hub'
                script {
                    dockerPush("notes-app","latest","mashoodk") 
                }
            }
        }
        stage('Deploy'){
            steps {
                script{
                   dockerCompose() 
                }
            }
        }
    }
}
