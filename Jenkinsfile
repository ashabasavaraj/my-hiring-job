@Library ('my-libs') _

pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
            git branch: 'main', credentialsId: 'git_cred', url: 'https://github.com/ashabasavaraj/my-hiring-job'
            }
        }
        stage('maven package') {
            steps {
            sh "mvn clean package"    
            
            }
        }
         stage('Tomcat Deploy') {
            steps {
            tomcatDeploy('172.31.28.5', 'jenkins-to-tomcat','ec2-user')
            }
        }
        
    }
}
