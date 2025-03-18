pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                script{
                    build()
                }
            }
        }
        stage('Deploy to DEV') {
            steps {
                deploy("DEV", 1010) 
            }
        }
        stage('Tests on DEV') {
            steps {
                testing("DEV")
            }
        }
        stage('Deploy to STG') {
            steps {
                deploy("STG", 2020)
            }
        }
        stage('Tests on STG') {
            steps {
                testing("STG")
            }
        }
        stage('Deploy to PRD') {
            steps {
                deploy("PRD", 3030)
            }
        }
        stage('Tests on PRD') {
            steps {
                testing("PRD")
            }
        }
    }
}

def build(){
    echo "Building of node application is satrting.."
    bat "npm install"
}

def deploy(String environment, int port){
    echo "Deployment to ${environment} has started.."
    bat "pm2 delete \"books-${environment}\""
    bat "pm2 start -n \"books-${environment}\" index.js -- ${port}"
}

def testing(String environment){
    echo "Testing on ${environment} has started.."
}