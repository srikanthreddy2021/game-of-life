node ('ecomm') {
    stage ('git'){
        git 'https://github.com/srikanthreddy2021/game-of-life.git'
    }
    stage ('maven') {
        sh 'mvn clean package'
    }
    stage ('archive artifacts'){
        artifacts: 'gameoflife-web/targets/gameoflife.war'
    }
}