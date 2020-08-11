
pipeline {
    environment{
    registry = "d3athstalker/hackathon"
    registryCredential = "docker_hub_d3athstalker"
    dockerImage = ''
  }
  agent any
  parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }
  stages {
    stage('git') {
      steps {
        echo 'checkout code from github'
        git branch: "${params.BRANCH}", url: 'https://github.com/pranshulgupta/shopping-cart.git'
      }
    }
     stage('install dependendience') {
      steps {
          echo 'installing dependencies'
          sh 'npm install'
        
            }
    }
     stage('build the project') {
      steps {
        echo 'building ..........'
        sh 'npm run build'
       
      }
    }
     stage('Build docker image'){
      steps{
        echo "Building docker image"
        script{
          dockerImage = docker.build registry + ":$BUILD_NUMBER" 
        }
      }
    }
    stage('Push docker image'){
      steps{
        echo "Pushing docker image"
        script{
          docker.withRegistry('',registryCredential) {
            dockerImage.push()
            dockerImage.push('latest')
          }
        }
      }      
    }
     stage('Build docker image'){
      steps{
        echo "Building docker image"
        script{
          dockerImage = docker.build registry + ":$BUILD_NUMBER" 
        }
      }
    }
    stage('Push docker image'){
      steps{
        echo "Pushing docker image"
        script{
          docker.withRegistry('',registryCredential) {
            dockerImage.push()
            dockerImage.push('latest')
          }
        }
      }      
    }
        stage('Deploy to Dev'){   
      steps{
        echo "Deploying to dev environment"
        sh 'docker rm -f hackathon || true'
        sh 'docker run -d --name=hackathon -p 8081:8080 d3athstalker/hackathon'
        //sh 'npm start'
      }
    }
  }
}
