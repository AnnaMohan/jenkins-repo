pipeline {
    agent any
     environment {
            GITHUB_TOKEN = credentials('githubpat-jenkins-repo')
        }
    stages {
        stage ("Clone Repo"){
            steps{
            sh '''
            rm -rf jenkins-repo
            git clone https://github.com/AnnaMohan/jenkins-repo.git
            cd jenkins-repo
            git config user.name "AnnaMohan"
            git config user.email "annamohan3@gmail.com"
            '''
            }
        }
        stage('Create Branch and Change') {
            steps {
                script {
                    def timestamp = new Date().format("yyyyMMddHHmmss")
                    env.BRANCH_NAME = "feature/auto-change-${timestamp}"
                }
                sh '''
                cd jenkins-repo
                git checkout -b ${BRANCH_NAME}
                echo "Another automated change at $(date)" >> update.txt
                git add update.txt
                git commit -m "Automated update at $(date)"
                git push -u origin ${BRANCH_NAME}
                '''
            }
        }

        stage('Automated PR') {
            steps {
                sh '''
                cd jenkins-repo
                export GITHUB_TOKEN=${GITHUB_TOKEN}
                hub pull-request -m "Automated PR: Update on $(date)" -b main
                '''
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
