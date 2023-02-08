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
                sh 'ssh -i /var/lib/jenkins/workspace/First_Maven_project/harshalTomcat.pem ec2-user@54.164.214.8 \'rm -r /var/lib/jenkins/workspace/First_Maven_project/webapp/target/webapp\ \''
                sh 'rm /var/lib/jenkins/workspace/First_Maven_project/webapp/target/webapp.war'
                sh 'scp -o StrictHostKeyChecking=no -i /var/lib/jenkins/workspace/First_Maven_project/harshalTomcat.pem /var/lib/jenkins/workspace/First_Maven_project/webapp/target/webapp.war ec2-user@54.164.214.8:/opt/apache/webapps/'
                sh 'ssh -i /var/lib/jenkins/workspace/First_Maven_project/harshalTomcat.pem ec2-user@54.164.214.8 "./opt/apache/bin/shutdown.sh;  ./opt/apache/bin/startup.sh"'
            }
        }
    }
}

