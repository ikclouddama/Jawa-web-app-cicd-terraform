pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }
    environment{
        date= "1/5/2022"
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }

        // Stage3 : Publish the source code to Sonarqube
        stage ('Deploy'){
            steps {
                echo 'deploying'
                }

            }
        }

        
        
    }

