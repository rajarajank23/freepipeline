pipeline {
  agent any

  stages {
    stage('Checkout code') {
      git 'git clone https://github.com/rajarajank23/freepipeline.git'
    }

    stage('Build code') {
      sh 'mvn clean install'
    }

    stage('Deploy code') {
      // Get the EC2 instance ID
      def ec2InstanceID = sh(returnStdout: true, script: 'aws ec2 describe-instances | grep "i-05ef54f4d06b7573d" | awk \'{print $3}\'')

      // Create a SSH connection to the EC2 instance
      withCredentials([sshCredentials(credentialsId: 'ubuntu')]) {
        sh 'ssh -i ~/.ssh/id_rsa ubuntu@${i-05ef54f4d06b7573d} "cd /home/ubuntu/html && mvn clean install"'
      }
    }
  }
}
