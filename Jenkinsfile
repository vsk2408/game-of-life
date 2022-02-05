node() {
    stage('git') {
        git 'https://github.com/dummyrepos/game-of-life.git'
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
