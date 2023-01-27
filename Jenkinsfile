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
            
            sshagent(['tomcat-creds']) {
    // some block
    sh "echo iam doing replay demo"
     sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/CI-CD-deploy/target/*.war ec2-user@172.31.28.5:/opt/tomcat9/webapps/"
        
     sh " ssh ec2-user@172.31.28.5 /opt/tomcat9/bin/shutdown.sh "   
     sh " ssh ec2-user@172.31.28.5 /opt/tomcat9/bin/startup.sh " 
               }
            }
        }
        
    }
}
