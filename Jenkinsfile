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
				sleep 81
				echo 'Launch agent'
				sh 'ssh -i /home/regression/.ssh/test_rsa vsee@10.10.40.250 "cd /Users/vsee/ && curl -O http://10.10.40.249:8080/jnlpJars/agent.jar && java -jar agent.jar"'
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