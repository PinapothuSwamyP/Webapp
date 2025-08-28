pipeline {
    agent any  
    tools {
        jdk 'Java_17'     // Use the name defined in "Global Tool Configuration"
    } 
    stages {
           stage('Build with Java 17') {
            steps {
                sh 'java -version'      // Should show Java 17
            }
        }
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
