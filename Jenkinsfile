pipeline {
  agent none
  options { 
    buildDiscarder(logRotator(numToKeepStr: '2'))
    skipDefaultCheckout true
  }
  stages {
    stage('Test-windows') {
      agent {
        kubernetes {
	  cloud 'kubernetes-windows'
          yamlFile 'windows/dotnet-pod.yaml'
        }
      }
      steps {
        bat 'dir'
        container(name:'windows-dotnet'){
          bat 'dotnet -h'
      } 
     }
    }
  }
}
