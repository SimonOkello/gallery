pipeline {
  agent any
    
  tools {nodejs "Node-20"}
    
  stages {
        
    stage('Clone Repository') {
      steps {
        // Clone Gallery repository from github.com
        git 'https://github.com/SimonOkello/gallery.git'
      }
    }
     
    stage('Build') {
      // Install Gallery dependencies
      steps {
        sh 'npm install'
      }
    }  
    stage('Deploy to Render') {
      steps {
        // Deploy to render.com
        sh curl 'https://api.render.com/deploy/srv-ck2p456ru70s73949ti0?key=nFak1ZFxXnA'
      }
    }
  }
}