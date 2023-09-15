pipeline {
  agent any

  stages {
    stage('clone repo and clean it') {
         steps (
              sh 'rm -rf pipe'
              sh 'git clone https://github.com/rajarajank23/freepipeline.git'
              sh 'mvn clean -f pipe'
         }

    }

           stage('Deploy to EC2') {

            steps {

                script {

                    // Define your EC2 instance SSH connection details

                    def remoteUser = 'ubuntu'

                    def remoteHost = '54.169.238.200'

                    def remoteDir = '/home/ubuntu/myprod'

                    

                    // Copy your code to the EC2 instance using SSH

                    sh "rsync -avzr --update -e "ssh -v -o StrictHostKeyChecking=no" $WORKSPACE/freepipeline/ ubuntu@54.169.238.200:/home/ubuntu/html
"

                }

            }

        }

    }

}
