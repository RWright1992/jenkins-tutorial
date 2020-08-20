pipeline{
        agent any
        stages{
        stage('Clone Repo'){
                steps{
                sh 'if ! [ API-Test ]; then git clone https://github.com/RWright1992/API-Test.git fi'
                }
	}
        stage('Install Docker + Docker Compose'){
                steps{
                sh 'curl https://get.docker.com | sudo bash && sudo apt update && sudo apt install -y curl jq && version=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r '.tag_name') && sudo curl -L "https://github.com/docker/compose/releases/download/${version}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose'
                }
	}
        stage('Deploy'){
                steps{
                sh 'sudo docker-compose up -d'
                }
	}
	}
}
