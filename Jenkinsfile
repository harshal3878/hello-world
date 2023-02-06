pipeline {
    agent { label any }
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/test-branch']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/harshal3878/hello-world.git']]])
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}

