pipeline {
    agent any

    stages {
        stage('maven package') {
            when {
            branch 'develop'
            }
            
            steps {
            sh "mvn clean package"    
            
            }
        }
         stage('Tomcat Deploy-dev') {
             when {
            branch 'develop'
            }  
            steps {
             echo "deploying to dev"
            }
         }
            stage('Tomcat Deploy-prod') {
             when {
            branch 'main'
            }  
            steps {
             echo "deploying to production"
            }
         }  
       }
        
    }

