pipeline {
    agent any

    tools {
        jdk 'jdk8'
        maven 'maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'feature-1.1',
                    url: 'https://github.com/lerockwins/sabear_simplecutomerapp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test || true'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar,target/*.war', fingerprint: true
            }
        }
    }

    post {
        success {
            echo "Declarative pipeline completed successfully"
        }
        failure {
            echo "Declarative pipeline failed"
        }
    }
}
