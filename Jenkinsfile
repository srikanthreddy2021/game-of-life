pipeline {
    agent {label 'ecomm'}
    stages {
        stage ('scm') {
            steps {
            git 'https://github.com/srikanthreddy2021/game-of-life.git'
            }
        }
        stage ('build') {
            steps {
                sh script: 'mvn clean package'
            }
        }
        stage ('post build') {
            steps {
                junit 'gameoflife-web/target/surefire-reports/*.xml'
                archiveArtifacts 'gameoflife-web/target/*.war'
            }
        }
    }
}