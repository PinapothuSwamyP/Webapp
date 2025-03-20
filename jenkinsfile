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
    }
}
