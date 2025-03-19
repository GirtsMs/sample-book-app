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
                script{
                    deploy("DEV", 1050)
                } 
            }
        }
        stage('Tests on DEV') {
            steps {
                script{
                    testing("DEV")
                }
            }
        }
        stage('Deploy to STG') {
            steps {
                script{
                    deploy("STG", 2020)
                }
            }
        }
        stage('Tests on STG') {
            steps {
                script{
                    testing("STG")
                }
            }
        }
        stage('Deploy to PRD') {
            steps {
                script{
                    deploy("PRD", 3030)
                }
            }
        }
        stage('Tests on PRD') {
            steps {
                script{
                    testing("PRD")
                }
            }
        }
    }
}

def build(){
    echo "Building of node application is satrting.."
    bat "npm install"
    bat "pm2 --version"
}

def deploy(String environment, int port){
    echo "Deployment to ${environment} has started.."
    bat "pm2 delete \"books-${environment}\""
    bat "pm2 start -n \"books-${environment}\" index.js -- ${port}"
}

def testing(String environment){
    echo "Testing test set on ${environment} has started.."
    git branch: 'main', url: 'https://github.com/GirtsMs/api-automation.git'
    bat "npm install"
}