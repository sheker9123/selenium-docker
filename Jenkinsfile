pipeline {
    agent none
    stages {
        stage('Build Jar') {
            agent {
                docker {
                    image 'maven:3-alpine'
                    args '-v $HOME/.m2:/root/.m2'
                }
            }
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Build Image') {
            steps {
                script {
                	app = docker.build("s.com/selenium-docker")
                }
            }
        }
        stage('Push Image') {
            steps {
                script {
			app.push("latest")
                }
            }
        }
    }
}
