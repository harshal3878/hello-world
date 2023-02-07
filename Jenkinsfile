pipeline {
    agent any
    
    tools {
        maven 'Maven'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/test-branch']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/harshal3878/hello-world.git']]])
            }
        }
        stage('Build') {
            steps {
                sh 'who'
                sh 'mvn clean install'
                sh 'echo "build successful"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'scp -i /home/ec2-user/harshalTomcat.pem /var/lib/jenkins/workspace/First_Maven_project/webapp/target/webapp.war ec2-user@100.25.151.73:/home/ec2-user/webapp.war'
            }
        }
    }
}

