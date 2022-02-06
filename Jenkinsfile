pipeline {
    agent {label 'ecomm'}
    triggers {
        cron('H * * * 1-5')
    }
    parameters {
        string(name: 'MAVENGOAL', defaultvalue: 'clean package', description: 'Enter your option')
    }
    options {
        timeout(time:30, unit:'MINUTES')
    }
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
                stash name: 'warfile', includes: 'gameoflife-web/target/*.war'
            }
        }
        stage ('copy to other node') {
            agent { label 'ltelog'}
            steps {
                unstash name: 'warfile'
                sh script 'echo you can deploy your file using ansible or terraform now'
            }
        }
    }
}