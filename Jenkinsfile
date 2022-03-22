pipeline{
  agent any
  
  environment{
    dockerImage=''
    registry='jyothiswaroopreddy08/devops-project'
    registryCredential='dockerhub_id'
  }
  
  stages{
//     stage('Checkout') {
//       steps{
//         git credentialsId: 'jyothi', url: 'git@github.com:jyothiswaroopreddy08/devops-project.git'
//       }
//      }
  stage('Build'){
      steps{
        bat "mvn install"
      }
    }
    
    stage('Test'){
      steps{
        bat "mvn test"
      }
    }
    stage('Package'){
      steps{
        bat "mvn package"
      }
    }
    
    stage('Build Docker Image') {
            steps {
                script {
                  dockerImage = docker.build registry
                }
            }
    }
    stage('Deploy our image') {
          steps{
            script {
                docker.withRegistry( '', registryCredential ) {
                dockerImage.push()
                }
            }
         }
      }
    stage("Run Docker Container"){
      steps{
        script{
          dockerImage=docker.run -d -p 8000:8080 registry
        }
      }
    }

    
  }
}
