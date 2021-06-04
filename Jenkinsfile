pipeline {
  agent any

  stages {

    stage ('Get Source'){
      steps {
        git url: 'https://github.com/atoumdesign/pedelogo-catalogo.git', branch: 'main'
        sh 'pwd'
        sh 'ls'
        echo("BUILD_NUMBER=${env.BUILD_NUMBER}")
        echo("BUILD_ID=${env.BUILD_ID}")
        echo("LOADED_BUILD_NUMBER=${env.LOADED_BUILD_NUMBER}")
        
      }
    }

    stage ('Docker Build'){
      steps {
        script {
          sh 'docker'
          sh 'pwd'
          sh 'ls'
          dockerapp = docker.build("atoumdesign/pedelogo-catalogo", '-f src/PedeLogo.Catalogo.Api/Dockerfile .')

        }
      }
    }
/*
    stage ('Docker Push Image'){
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
          dockerapp.push('latest')
          dockerapp.push("${env.BUILD_ID}")
        }
      }
    } */
  }
}
