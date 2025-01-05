pipeline {
    environment {
    imagename = "backend"
    jenkinsProject = 'calculator-webapp-backend'
  }

    agent any
    stages {

        stage('Git Staging'){

            steps{

                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-cred', url: 'https://github.com/akhildevops-practice/Prac-jenkins-con.git']]])

            }
        }


        stage('Build image and Run image ') {

            steps{
                sh 'sudo su - jenkins -s/bin/bash'
                //sh 'sudo docker stop $imagename'
                //sh 'sudo docker rm $imagename'
                //sh 'sudo docker rmi $imagename'
                sh 'sudo docker image build -t  $imagename .'

            }

        }
        
        stage('Run image ') {

            steps{
                sh 'sudo docker run -p 5000:5000 --restart=always --name $imagename  -itd $imagename'

            }

        }
        

        
    }
}
