pipeline {
    agent any
    environment{
        DOCKERHUB_CREDS = credentials('1')
    }
    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
                sh 'ls *'
            }
        }
        stage('Build Image') {
            steps {
                //Aquí debes poner tu github
		sh 'docker build -t https://github.com/AlexRodriguezFortanet/EjermploDockerHub_AlejandroRodriguez.git .'
            }
        }
        stage('DockerHUB Login') {
            steps {
                
                sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'                
                }
            }
        stage('Docker Push') {
            steps {
		//Aquí debes poner tu github
                sh 'docker push alexrodriguezfortanet/dockerhub'
                }
            }
        }
    post {
		always {
			sh 'docker logout'
		}
	 }
    }

