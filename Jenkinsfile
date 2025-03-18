pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'Building of node application is starting...'
            }
        }
        stage('Deploy to DEV') {
            steps {
                deploy("DEV")
            }
        }
        stage('Tests on DEV') {
            steps {
                testing("DEV")
            }
        }
        stage('Deploy to STG') {
            steps {
                deploy("STG")
            }
        }
        stage('Tests on STG') {
            steps {
                testing("STG")
            }
        }
        stage('Deploy to PRD') {
            steps {
                deploy("PRD")
            }
        }
        stage('Tests on PRD') {
            steps {
                testing("PRD")
            }
        }
    }
}

def deploy(String environment){
    echo "Deployment to ${environment} has started.."
}

def testing(String environment){
    echo "Testing on ${environment} has started.."
}