pipeline {
    agent {
        node {
           label 'master'
        }

}

    stages {
        stage('Build sa-frontend') {
            steps {
                echo 'Building..'
            }
        }
        stage('Build sa-webapp') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Build Docker sa-frontend') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Build Docker sa-webapp') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Build Docker sa-logic') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Push to registry') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
