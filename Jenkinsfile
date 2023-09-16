pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out your source code repository here
                // For example, if you're using Git:
                git branch: 'pipe', url: 'https://github.com/rajarajank23/freepipeline.git'
            }
        }
        
        stages {
        stage('Deploy to EC2') {
            steps {
                script {
                    // Define your EC2 instance's SSH credentials
                    def remoteUser = 'ubuntu'
                    def remoteHost = '54.169.238.200'
                    def sshKey = credentials('ubuntu') // Replace with your SSH credentials ID in Jenkins
                    
                    // SSH into the EC2 instance and execute the script
                    sshScript(
                        remoteUser: ubuntu,
                        remoteHost: 54.169.238.200,
                        keyFile: sshKey,
                        script: 'bash /home/ubuntu/myprod'
                    )
                }
            }
        }
    }
}
