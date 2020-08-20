pipeline{
        agent any
        stages{
        stage('Clone Repo'){
                steps{
                sh 'git fetch https://github.com/RWright1992/API-Test.git && cd API-Test'
                }
	}
        stage('Install Docker + Docker Compose'){
                steps{
		sh 'sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose'
                }
	}
        stage('Deploy'){
                steps{
                sh 'sudo docker-compose up -d'
                }
	}
	}
}
