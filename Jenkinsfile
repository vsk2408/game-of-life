node() {
    stage('git') {
        git 'https://github.com/vsk2408/game-of-life.git'
    }
    stage('build') {
        sh 'mvn package'
    }
    stage('testresults'){
        junit 'gol/target/surefire-reports/*.xml'
    }
    stage('archiveartifacts') {
        archiveArtifacts artifacts: 'gol/target/*.war', followSymlinks: false
    }
}
