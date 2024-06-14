pipeline{
	agent any
	triggers{
		pollSCM '*/5 * * * *'
	}
	stages {
		stage('Build'){
			steps {
			sh '''
			docker compose up
			'''
			}
		}
		stage('Test') {
			steps {
			sh '''
			apt update -y
			apt upgrade -y
			apt-get install python3-pip -y
			python3 -m venv /venv
			. /venv/bin/activate
			pip install pytest selenium -y
			docker compose up
			sleep 15
			python test_devopstest.py
			'''
			}
		}
	}
}
