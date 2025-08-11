pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sshagent(['tomcat-ssh-key']) {
                    sh '''
                        # Copy WAR to Tomcat webapps folder
                        scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.40.174:/opt/tomcat/webapps/
                        
                        # Optionally restart Tomcat
                        # ssh -o StrictHostKeyChecking=no ec2-user@<TOMCAT_SERVER_IP> "sudo systemctl restart tomcat"
                    '''
                }
            }
        }
    }
}
