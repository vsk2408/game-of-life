node() {
    stage('git') {
        git 'https://github.com/vsk2408/game-of-life.git'
    }
    stage('build') {
        sh 'mvn package'
    }
    stage('testresults'){
        junit 'gameoflife-web/target/surefire-reports/*.xml'
    }
    stage('archiveartifacts') {
        archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
    }
}
