pipeline {
    agent none

    stages {
        stage('Pre Test 1') {
            agent { 
                label 'test master'
            }
            steps {
                echo 'Restart and wait'
				sh 'uname -a'
				sh '/usr/bin/sshpass -f passFile ssh regression@10.10.2.32 vim-cmd vmsvc/power.reset 14'
				sleep 120
            }
        }
        stage('Pre Test 2') {
            agent { 
                label 'master'
            }
            steps {
                echo 'Start agent'
				sh 'uname -a'
				sh 'ssh -i /var/lib/jenkins/.ssh/test_rsa vsee@10.10.40.233 "cd /Users/vsee/thanh/ && curl -O http://10.10.40.249:8080/jnlpJars/agent.jar && java -jar agent.jar"'
            }
        }
        stage('Test') {
            agent { 
                label 'Katalon-Mac01'
            }
            steps {
                echo 'Testing..'
            }
        }
        stage('Post Test') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}