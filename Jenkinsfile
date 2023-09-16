pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out your source code repository here
                // For example, if you're using Git:
                git branch: 'pipe', credentialsId: 'mygithub', url: 'https://github.com/rajarajank23/freepipeline.git'
            }
        }
        
        stage('Deploy to EC2') {
            steps {
                script {
                    // Define your EC2 instance's SSH credentials
                    def remoteUser = 'ubuntu'
                    def remoteHost = '54.169.238.200'
                    def remoteKey = credentials('ubuntu') // Add your SSH credentials in Jenkins
                
                    // SSH into the EC2 instance and copy the code
                    sh """\
                       sshagent(credentials: ['ubuntu']) {
                       sh 'ssh -o StrictHostKeyChecking=no ubuntu@54.169.238.200 "bash /home/ubuntu/html"'
                    """
                }
            }
        }
    }
}

