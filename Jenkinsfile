pipeline {
    agent any
    tools {
        // This must exactly match the Maven name in Global Tool Configuration
        maven 'Maven 3.6.3'
    }
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
    }
}
