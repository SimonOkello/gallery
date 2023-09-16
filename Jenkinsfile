pipeline {
  agent any
    
  tools {nodejs "Node-20"}
    
  stages {
        
    stage('Clone Repository') {
      steps {
        git 'https://github.com/SimonOkello/gallery.git'
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }  
    
            
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Deploy') {
      steps {
        sh curl 'https://api.render.com/deploy/srv-ck2p456ru70s73949ti0?key=nFak1ZFxXnA'
      }
    }
  }
  post {
        failure {
            // Send a Slack notification on build failure
            slackSend(channel: '#playground', color: 'danger', message: 'Test build failed! Check the Jenkins job for details.')
        }
        success {
            // Send a Slack notification on build success
            slackSend(channel: '#playground', color: 'good', message: 'Test build succeeded!')
            
        }
    }
}