pipeline {
    agent any

    stages {

        stage('checkout') {

			steps {
			git branch: 'feature/commercial-card-fritz', credentialsId: 'github', url: 'https://github.com/DEL-ORG/commercial-card.git'
			}
        }
    }
}