pipeline {
    agent {
        node {
           label 'master'
        }

}

    stages {
        stage('Build sa-frontend') {
            steps {
                sh 'cd ${WORKSPACE}/sa-frontend && npm install && npm run build'
            }
        }
        stage('Build sa-webapp') {
            steps {
                sh 'cd ${WORKSPACE}/sa-webapp && mvn install'
            }
        }
        stage('Build Docker sa-frontend') {
            steps {
                sh 'cd ${WORKSPACE}/sa-frontend && docker build -t sa-frontend:latest .'
            }
        }
        stage('Build Docker sa-webapp') {
            steps {
                sh 'cd ${WORKSPACE}/sa-webapp && docker build -t sa-webapp:latest .'
            }
        }
        stage('Build Docker sa-logic') {
            steps {
                sh 'cd ${WORKSPACE}/sa-logic && docker build -t sa-logic:latest .'
            }
        }
        stage('Push to registry') {
            steps {
                sh '''docker tag sa-frontend:latest mrinal08/sa-frontend:latest
		docker tag sa-webapp:latest mrinal08/sa-webapp:latest
		docker tag sa-logic:latest mrinal08/sa-logic:latest
		cat /var/lib/jenkins/pass.txt | docker login --username mrinal08 --password-stdin
		docker push mrinal08/sa-frontend:latest
		docker push mrinal08/sa-webapp:latest
		docker push mrinal08/sa-logic:latest'''
            }
        }
    }
}
