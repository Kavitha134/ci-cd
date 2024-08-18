pipeline{
    agent any
    
    stages{
        
        stage('checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Kavitha134/ci-cd']])
                echo 'checkout completed'
            }
        }
        
        stage('build docker'){
            steps{
                script{
                    sh 'docker build -t ankavitha/todoapp1 .'
                }
                
            }
        }
        stage('push the docker'){
            steps{
                script{
                    sh '''docker login -u ankavitha -p Kavitha100%
                    docker push ankavitha/todoapp1:latest'''
                }
            }
        }
    }
}
