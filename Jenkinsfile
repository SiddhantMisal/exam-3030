pipeline {
    agent any

    stages {
        stage('Pull data form git') {
            steps {
                git branch: 'master', url: 'https://github.com/SiddhantMisal/exam-3030.git'
            }
        }
        
        stage('Build Image') {
            steps {
                sh 'ls -l'
                sh 'docker build -t siddhant1001/nginx .'
            }
        }
        
        stage('push image') {
            steps {
                sh 'docker push siddhant1001/nginx'
            }
        }

        stage('remove existing service') {
            steps {
                sh 'docker service rm --force nginx'
            }
        }
        
	stage('create service') {
            steps {
                sh 'docker service create --name nginx  -p 5000:5000 --replicas 5 siddhant1001/nginx'
            }
        }
    }
}
