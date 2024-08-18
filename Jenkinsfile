pipeline{
    agent any
    stages{
        stage('checkout the git repo'){
            steps{
                git credentialsId: 'd1755d17-e25c-4203-8cb5-da8f842efc21', 
                url: 'https://github.com/Kavitha134/jenkins1',
                branch: 'main'
            }
        }
        stage('Update K8S manifest & push to Repo'){
            steps {
                script{
                    withCredentials([usernamePassword(credentialsId: 'd1755d17-e25c-4203-8cb5-da8f842efc21', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh '''
                        cd argocd1
                        cat deploy.yaml
                        sed -i "s/latest/10/g" deploy.yaml
                        cat deploy.yaml
                    
                        git remote set-url origin https://d1755d17-e25c-4203-8cb5-da8f842efc21@github.com/Kavitha134/jenkins1.git
                        git add deploy.yaml
                        git commit -m 'Updated the deploy yaml | Jenkins Pipeline'
                        git remote -v
                        git config --global user.name "${GIT_USERNAME}"
                        git config --global user.password "${GIT_PASSWORD}"
                        git push https://github.com/Kavitha134/jenkins1.git HEAD:main
                        '''                        
                    }
                }
            }
        } 
        
    
    }
}
