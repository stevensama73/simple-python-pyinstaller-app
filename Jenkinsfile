pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'python:3.12.0a4-bullseye'
                }
            }
            steps {
                sh 'python -m py_compile app.py'
            }
        }
    }
}