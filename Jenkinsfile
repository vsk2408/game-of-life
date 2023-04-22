Pipeline{
    agent any
    
    stage('git') {
        checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vsk2408/game-of-life/']])
    }
    stage('build') {
        sh 'mvn package'
    }
    stage('Static Code Analysis') {
      environment {
        SONAR_URL = "http://15.206.212.53:9000/"
      }
      steps {
        withCredentials([string(credentialsId: 'sonarqube', variable: 'SONAR_AUTH_TOKEN')]) {
          sh 'mvn sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}'
        }
      }
    }
    stage('Docker hub'){
        sh 'docker build -t game-of-life .'
    }
}
