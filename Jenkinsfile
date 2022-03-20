pipeline{
  agent any
  
  stages{
    stage('Checkout') {
      steps{
        git credentialsId: 'jyothi', url: 'git@github.com:jyothiswaroopreddy08/devops-project.git'
      }
     }
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
                  sh 'docker build -t devopshint/my-app-1.0 .'
                }
            }
    }
      stage('Deploy Docker Image') {
            steps {
                script {
                 sh 'docker push devopshint/my-app-1.0'
                }
            }
        }
    
  }
}
