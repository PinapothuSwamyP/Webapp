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
                withMaven(maven: 'mvn') { // Use the name from Global Tool Configuration
            sh 'mvn clean package'

            }
        }
    }
}
