pipeline {
  agent {
    docker { image 'docker:windowsservercore-ltsc2025' } //docker pull docker:windowsservercore-ltsc2025
    python { image 'python:3.11-slim' }
  }

  environment {
     docker_repo = "docker.io"
     docker_image = "nachiyar/myapp"
     docker_tag = ${BUILD_NUMBER}
     //config_map 
  }

  stages{

    stage('Checkout') {
        steps {
            git -b main https://github.com/Nachiyar2702/equalexperts.git
        }
    }

    stage('Run Unit Test'){
       
            steps {
                try{
                      sh 'pytest -q --exitcode==1 '
                      echo "Tests passed and proceeding "
                } 
                catch{
                    echo "Tests failed and Aborting the pipeline"
                    currentBuild.status = Failure
                }
            }  
    }
    // stage('Build Docker') {
    //     steps{

    //     }


    // }

}

