pipeline {
  agent any

  stages {
    stage('git update') {
      steps{
        git url: 'https://github.com/chanhyuk0919/kakaodevpipeline.git', branch: 'main'
      }
    }
  }
    stages {
    stage('docker image build and push') {
      steps{
        sh '''
        sudo docker build -t dlcksgur0919/kakaodev:yellow
        sudo docker push dlcksgur0919/kakaodev:yellow
        '''  
      }
    }
  }
    stages {
    stage('k depoly svc') {
      steps{
        sh '''
        ssh 211.183.3.100 'k create deplpy deploy-yellow --image=dlcksgur0919/kakaodev:yellow'
        ssh 211.183.3.100 'k expose deploy deploy-yellow --type=NodePort --port=8084 \ --target-port=80 --name=deploy-yellow-
        '''

    
      }
    }
  }

  


}
