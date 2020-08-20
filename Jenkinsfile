pipeline{
        agent any
        stages{
        stage('Clone Repo'){
                steps{
                sh 'git fetch https://github.com/RWright1992/API-Test.git'
                }
	}
        stage('Install Docker + Docker Compose + Pytest'){
                steps{
		sh 'curl https://get.docker.com | sudo bash'
		sh 'sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
		sh 'sudo chmod +x /usr/local/bin/docker-compose'
		sh 'pip3 install pytest'
		sh 'pip3 install Flask-Testing'
                }
	}
	stage(Test){
		steps{
		sh 'cd API-Test/service1 && pip3 install -r requirements.txt'
		sh 'cd API-Test/service1 && python3 -m pytest'
		sh 'cd ..'
		sh 'cd API-Test/service2 && python3 -m pytest'
		}
	}
        stage('Deploy'){
                steps{
		sh 'pwd'
                sh 'cd .. && sudo docker-compose up -d'
                }
	}
	}
}
