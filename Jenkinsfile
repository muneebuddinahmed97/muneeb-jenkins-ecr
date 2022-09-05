pipeline {
    agent any
    tools {nodejs "node16" }
    environment {
        NODE_ENV='production'
    }
    
  
    stages {
        stage('source') {
            steps {
               git 'https://github.com/MahnoorAli02/jenkins-ecr.git'
               sh 'cat index.js'
            }
            
        }
        
         stage('build') {
             environment{
                 NODE_ENV='StagingGitTest'
             }
             
            
            steps {
             echo NODE_ENV
             withCredentials([string(credentialsId: 'd5e09baa-a871-4dbe-8007-bfe115ef26eb', variable: 'secver')]) {
                // some block
                echo secver
            }
                         sh 'npm install'
            }
            
        }
        
         stage('saveArtifact') {
            steps {
              archiveArtifacts artifacts: '**', followSymlinks: false
            }
            
        }
        
        
        
    }
}
