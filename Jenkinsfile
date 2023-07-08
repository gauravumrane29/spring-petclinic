pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                git branch: main, url: 'https://github.com/gauravumrane29/spring-petclinic.git', credentialsId: 'GithubToken'
            }
        }
        }
    }
