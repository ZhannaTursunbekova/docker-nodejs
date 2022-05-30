pipeline {
    agent any

    stage('Docker Build') {
        
        steps {
        sh 'docker build -t jannadev/nodejs_web_app:latest .'
      }
    }

    stage('Docker Push') {

      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerhubPassword', usernameVariable: 'dockerhubUser')]) {
          sh "docker login -u ${env.dockerhubUser} -p ${env.dockerhubPassword}"
          sh 'docker push jannadev/nodejs_web_app:latest'
        }
      }
    }
}