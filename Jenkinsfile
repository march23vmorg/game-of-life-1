pipeline{
    agent {label 'maven-jdk8'}
    stages{
        stage('vcs') {
            steps{
                git url: 'https://github.com/march23vmorg/game-of-life-1.git' ,
                branch: 'declarative'
            }    
        }
        stage('package'){
            tools{
                jdk 'jdk-8'
            }
            steps{
                sh 'mvn package'
            }
        }
        stage('post build'){
            steps{
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml' 
            }
        }
    }
}