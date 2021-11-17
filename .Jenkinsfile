pipeline {

  agent {
    docker { image 'node:14-alpine' }
  }

  stages {
    stage('Checkout Source') {
      steps {
        git url:'https://github.com/EtiennePS/win11React.git', branch:'master'
      }
    }
    
    stage("Build app") {
      steps {
          script {
              sh 'npm install'
              sh 'npm run build'
          }
      }
    }

    stage("Build image") {
      steps {
          script {
              myapp = docker.build("etienneps/win11react:${env.BUILD_ID}")
          }
      }
    }
    
      /*stage("Push image") {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                            myapp.push("latest")
                            myapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }

    
    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "win11react.yml", kubeconfigId: "mykubeconfig")
        }
      }
    }*/

  }

}