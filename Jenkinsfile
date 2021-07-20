pipeline {
  environment {
    registry_search = "hub.cxview.ai/search_searching_staging"
    registry_service = "hub.cxview.ai/services_searching_staging"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/Duocc-mcq/Tim-hieu-docker.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          docker.withRegistry( 'https://hub.cxview.ai', registryCredential ) {
            dockerImage = docker.build registry_search + ":$BUILD_NUMBER"
            dockerImage.push() 
            dockerImage.push('latest') 
          }
        }
      }
      steps{
        script {
          docker.withRegistry( 'https://hub.cxview.ai', registryCredential ) {
            dockerImage = docker.build registry_service + "$BUILD_NUBER"
            dockerImage.push()
            dockerImage.push('latest') 
          }
        } 
      }
    }
    stage('Deploy Image_search') {
      steps{
        script {
          sh ""
        }
      }
    }

    stage('Deploy Image_service') {
      steps{
        script {
          sh ""
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
