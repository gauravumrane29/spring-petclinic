pipeline{
    agent any
    stages{
        stage('git checkout'){
            deleteDir()
            checkout([$class: 'GitSCM',
            branches: [[name: 'main']],
            extensions: [[$class: 'WipeWorkspace']],
            userRemoteConfigs: [[url: 'git@github.com:gauravumrane29/spring-petclinic.git']]
            ])

        }
    }
}