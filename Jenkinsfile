pipeline{
  agent any
  
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
                  sh 'docker build -t devopshint/my-app-1.0 .'
                }
            }
    }
      stage('Deploy Docker Image') {
            steps {
                script {
                  withCredentials([string(credentialsId: 'jyothiswaroopreddy08', variable: 'dockerhubpwd')]) {
                  sh 'docker login -u devopshint -p ${dockerhubpwd}'
}
                 sh 'docker push devopshint/my-app-1.0'
                }
            }
        }
    
  }
}
