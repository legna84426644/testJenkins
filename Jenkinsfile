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
				/usr/bin/sshpass -f /home/regression/passFile ssh regression@10.10.2.32 vim-cmd vmsvc/power.reset 14
				sleep 180
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