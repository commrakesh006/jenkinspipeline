pipeline {
    agent any
    
    

    triggers {
         pollSCM('* * * * *') // Polling Source Control
     }

stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    
    stage('Deploy to stage'){
        steps{
         build job :'Deploy-to-staging'   
        }
    }
       
    }
}
