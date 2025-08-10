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
                withMaven(maven: '/usr/share/maven') { // Use the name from Global Tool Configuration
            sh 'mvn clean package'
                }
            }
        }
    }
}
