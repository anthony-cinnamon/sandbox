pipeline {
    agent { docker { image 'python:3.5.1' label 'slave' } }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
		sh 'echo "Hello World"'
            }
        }
    }
}

