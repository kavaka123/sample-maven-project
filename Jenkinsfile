pipeline {
    agent any
    tools {
        maven 'maven-jenkins'
        jdk 'openjdk8'
    }
    
    stages{
        stage('Git clone'){
            steps {
                script {
                    git url: 'https://github.com/kavaka123/sample-maven-project.git'
                }
            }
        }
        
        stage('Initialize'){
            steps {
                sh '''
                   echo "PATH=${PATH}"
                   echo "M2_HOME=${M2_HOME}"
                   '''
            }
        }
        
        stage('Maven build'){
            steps {
                sh 'mvn clean compile test deploy'
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml'
                }
            }
        }
    }
}
