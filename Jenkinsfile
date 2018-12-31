pipeline {
    agent none

    stages {
        stage('Pre Test') {
            agent { 
                label 'test master'
            }
            steps {
                echo 'Building..'
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
				sh 'cd /Users/vsee'
				sh 'test.sh'
            }
        }
        stage('Post Test') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}