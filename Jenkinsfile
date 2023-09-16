pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'pipe', credentialsId: 'mygithub' url: 'https://github.com/rajarajank23/freepipeline.git'
            }
        }

stage('Deploy') {
            steps {
                sshagent(credentials: ['ubuntu']) {
                    sh 'rsync -avz  -e "ssh -o StrictHostKeyChecking=no" ./ ubuntu@54.169.238.200:/home/ubuntu/myprod'
                }
            }
        }
        
        stage('Deploy to EC2') {
            steps {
                
                       sshagent(credentials: ['ubuntu']) {
                       sh 'ssh -o StrictHostKeyChecking=no ubuntu@54.169.238.200 "/home/ubuntu/myprod"'
                    
                }
            }
        }
    }
}
