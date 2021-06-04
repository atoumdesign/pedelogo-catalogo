pipeline {
  agent any

  stages {

    stage ('Get Source'){
      steps {
        git url: 'https://github.com/atoumdesign/pedelogo-catalogo.git', branch: 'main'
      }
    }

    stage ('Docker Build'){
      steps {
        script {
          dockerapp = docker.build("atoumdesign/pedelogo-catalogo:${env.BUILD_ID}", '-f ./src/Pe>
        }
      }
    }

    stage ('Docker Push Image'){
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
          dockerapp.push('latest')
          dockerapp.push("${env.BUILD_ID}")
        }
      }
    }
  }
}
