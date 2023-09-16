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
    stage('Run Tests') {
      // Test Gallery app
      steps {
        sh 'npm test'
      }
    }  
    stage('Deploy to Render') {
      steps {
        // Deploy to render.com
        sh 'curl --request POST --url https://api.render.com/deploy/srv-ck2p456ru70s73949ti0?key=nFak1ZFxXnA'
      }
    }
  }
  post {
        failure {
            // Send a Slack notification on build failure
            slackSend(channel: '#playground', color: 'danger', message: "Gallery project build failed! Check the Jenkins job for details. Build #${env.BUILD_NUMBER} Build link: ${env.BUILD_URL} ")

            mail to: "simon.okello@student.moringaschool.com",
            subject: "Build #${env.BUILD_NUMBER} Failed",
            body: "Build #${env.BUILD_NUMBER} failed. Build link: ${env.BUILD_URL}"
        }
        success {
            // Send a Slack notification on build success
            slackSend(channel: '#playground', color: 'good', message: "Hi @Samuel Kadima SimonOkello's IP 1 is complete. Build #${env.BUILD_NUMBER} was successful. Gallery project has been deployed on Render!. Visit: https://gallery-tnbj.onrender.com")
            
        }
    }
}
