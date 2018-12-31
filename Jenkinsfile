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
				cd '/Users/vsee'
				java -jar remoting.jar -workDir /Users/vsee
            }
        }
        stage('Post Test') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}