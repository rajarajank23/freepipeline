pipeline {
  agent any

  stages {
    stage('clone repo and clean it') {
         steps (
              sh "rm -rf freepipe"
              sh "git clone https://github.com/rajarajank23/freepipeline.git"
              sh "mvn clean -f freepipe"
         }

    }

    stage('Test') {
         steps {
              sh "mvn test -f freepipe"
         }
    }

    stage('Deploy code') {
         steps {
              sh "mvn package -f freepipe"
          }
 
     }

      // Get the EC2 instance ID
      def ec2InstanceID = sh(returnStdout: true, script: 'aws ec2 describe-instances | grep "i-05ef54f4d06b7573d" | awk \'{print $3}\'')

      // Create a SSH connection to the EC2 instance
      withCredentials([sshCredentials(credentialsId: 'ubuntu')]) {
        sh 'ssh -i ~/.ssh/id_rsa ubuntu@${i-05ef54f4d06b7573d} "cd /home/ubuntu/html && mvn clean install"'
      }
    }
  }
}
