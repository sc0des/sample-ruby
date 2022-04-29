pipeline {
    agent any
    stages {
        stage('Pre-build') {
            steps {
                sh 'gem install sinatra -v1.4.8'
            }
        }
        stage('Build') {
            steps {
            sh 'run main.rb'
            }

        }
    }
}
