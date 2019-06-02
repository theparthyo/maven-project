pipeline{
    agent any
    tools{
        jdk 'java8'
        maven 'maven3'
    }
    stages{
        stage('init'){
            steps{
                echo "this is Init Stage"
            }
        }
        stage('build'){
            steps{
                echo "this is Build Stage"
                sh label: '', script: 'mvn clean package checkstyle:checkstyle'
            }
        }
        stage('deploy'){
            steps{
                echo "this is Deploy Stage"
            }
        }
    }

}