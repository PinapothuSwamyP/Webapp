pipeline {
    agent any
    tools {
        maven 'Maven 3.6.3'  // This name must match what you configured in Global Tool Configuration

    }
   stages {
        stage('Checkout Code') {
            steps {
               checkout scm
            }
        }

        stage('Build with Maven') {
            steps { 
                withMaven(maven: 'mvn') { // Use the name from Global Tool Configuration
            sh 'mvn clean package'
                }
            }
        }
    }
}
