pipeline {
    agent any

    stages {
        stage('maven package') {
           
            steps {
            sh "mvn clean package"    
            
            }
        }
         stage('Docker Build') {
             
            steps {
             sh " docker build -t asharaghu/hiring:0.0.2 ."
            }
         }
            stage('Docker Push') {
            steps {
             withCredentials([string(credentialsId: 'docker-hub', variable: 'hubpwd'), string(credentialsId: 'docker-hub', variable: 'hubpwd')]) {
                 sh "docker login -u asharaghu -p ${hubpwd}"
                 sh "docker push asharaghu/hiring:0.0.2"
               }
            }
         }
        stage('Docker Deploy') {
            steps {
                sshagent(['docker-host']) {
                sh 'ssh -o StrictHostKeyChecking=no ec2-user@172.31.30.215 docker run -p -d 8080:8080 --name hiring asharaghu/hiring:0.0.2
                }
            }
        }
    }
}

