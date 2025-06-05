pipeline {
    agent any
    stages {

        stage ("SCM"){
            steps{
            git url: 'https://github.com/AnnaMohan/basicassignment.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
