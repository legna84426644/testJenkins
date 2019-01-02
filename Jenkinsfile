pipeline {
    agent none

    stages {
        stage('Reset VM') {
            agent { 
                label 'test master'
            }
            steps {
                echo 'Restart and wait'
				sh 'who'
				sh 'uname -a'
				sh '/usr/bin/sshpass -f passFile ssh regression@10.10.2.32 vim-cmd vmsvc/power.reset 14'
				sleep 120
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