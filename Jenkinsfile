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
            post{
                success{
                    echo "checkstyle"
                    checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: 'Checkstyle', unHealthy: ''
                    echo "archive"
                    archiveArtifacts '**/*.war'
                    
                }
            }
        }
        stage('deploy'){
            steps{
                echo "this is Deploy Stage"
                timeout (time: 60, unit: 'SECONDS') {
                   input 'do you want run this job' 

                }
                echo "build test pacakage"
                    build 'dev_depoy'
            }
        }
    }

}