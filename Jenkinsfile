pipeline{
    agent any
    stages{
        stage('git checkout'){
            steps{
                deleteDir()
                checkout([$class: 'GitSCM',
                branches: [[name: 'origin/main']],
                extensions: [[$class: 'WipeWorkspace']],
                userRemoteConfigs: [[url: 'git@github.com:gauravumrane29/spring-petclinic.git']]
                ])
            }
        }
    }
}
