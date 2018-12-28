pipeline {
    agent none

    stages {
        stage('Pre Test') {
            agent { 
                label 'master'
            }
            steps {
                echo 'Building..'
				sh 'uname -a'
            }
        }
        stage('Test') {
            agent { 
                label 'Katalon-Mac01'
            }
            steps {
                echo 'Testing..'
				sh 'uname -a'
            }
        }
        stage('Post Test') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}