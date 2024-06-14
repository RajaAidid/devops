pipeline{
	agent any
	triggers{
		pollSCM '*/5 * * * *'
	}
	stages {
		stage('Build'){
			steps {
			sh '''
			docker compose up -d
			'''
			}
		}
		stage('Test') {
			steps {
			sh '''
			apt update -y
			apt upgrade -y
			apt-get install python3-pip -y
   			apt-get install python3-venv -y
			python3 -m venv venv
   			cd venv/bin
      			ls
			./activate
			pip install -y pytest selenium
			docker compose up -d
			sleep 15
			python3 test_devopstest.py
			'''
			}
		}
	}
}
