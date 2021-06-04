pipeline {
  agent any

  stages {

    stage ('Get Source'){
      steps {
        git url: 'https://github.com/atoumdesign/pedelogo-catalogo.git', branch: 'main'
        sh 'pwd'
        sh 'ls'
        echo("${env.BUILD_NUMBER}")
        echo("${a.LOADED_BUILD_NUMBER}")
        sh 'docker'
      }
    }

    stage ('Docker Build'){
      steps {
        script {
          sh 'pwd'
          sh 'ls'
          dockerapp = docker.build("atoumdesign/pedelogo-catalogo", '-f src/PedeLogo.Catalogo.Api/Dockerfile .')
          echo("${env.BUILD_NUMBER}")
          echo("${a.LOADED_BUILD_NUMBER}")
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
