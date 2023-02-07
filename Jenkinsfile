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
                sh 'scp -o StrictHostKeyChecking=no -i /var/lib/jenkins/workspace/First_Maven_project/harshalTomcat.pem /var/lib/jenkins/workspace/First_Maven_project/webapp/target/webapp.war ec2-user@100.25.151.73:/opt/apache-tomcat-8.5.85/webapps/docs/appdev/sample.war'
            }
        }
    }
}

