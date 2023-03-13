pipeline{
    agent {label 'maven-jdk8'}
    stages{
        stage('vcs'){
            git url 'https://github.com/march23vmorg/game-of-life-1.git' ,
                branch 'declarative'
        }
        stage('package'){
            steps{
                sh 'mavn package'
            }
        }
        stage('post build'){
            steps{
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/Test-*.xml' 
            }
        }
    }
}