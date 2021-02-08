pipeline{
    tools{
        jdk 'mymaven'
        maven 'mymaven'
    }
    agent none
    stages{
       stage('Compile'){
           agent any
           steps{
               sh 'mvn compile'
           }
       }
       stage('Testing'){
           agent any 
           steps{
               sh 'mvn test'
           }
           post{
               always{
                   junit 'gameoflife-web/target/surefire-reports/*.xml'
               }
           }
       }
       stage('Package'){
           agent {label 'Lin_Slave2'}
           steps{
               git 'https://github.com/Gopi757/game-of-life.git'
               sh 'mvn package'
           }
       }
    }
}
