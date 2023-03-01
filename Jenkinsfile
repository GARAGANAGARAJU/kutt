pipeline {
  agent any

  environment {
    NODE_VERSION = '14'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/develop']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/your-username/your-nextjs-app.git']]])
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'nvm install $NODE_VERSION'
        sh 'npm install'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }

    stage('Deploy') {
      steps {
        sh 'npx vercel --prod'
      }
    }
  }
}
