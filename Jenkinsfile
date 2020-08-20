pipeline{
        agent any
        stages{
        stage('Clone Repo'){
                steps{
                sh 'git fetch https://github.com/RWright1992/API-Test.git'
                }
	}
        stage('Install Docker + Docker Compose'){
                steps{
		sh 'curl https://get.docker.com | sudo bash && sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose'
                }
	}
	stage(Test){
		steps{
		sh 'pip install -U pytest && cd API-Test/service1 && pytest && cd .. && cd API-Test/service2 && pytest' 
		}
	}
        stage('Deploy'){
                steps{
                sh 'cd .. && sudo docker-compose up -d'
                }
	}
	}
}
