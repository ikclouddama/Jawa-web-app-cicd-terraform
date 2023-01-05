pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }
    environment{
        ArtifactId = readMavenPom().getArtifactId()
        GroupId = readMavenPom().getGroupId()
        Version = readMavenPom().getVersion()
        Name= readMavenPom().getName()
        
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
        // Publish to nexus
        stage('Publish to Nexus'){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: "${ArtifactID}", classifier: '', file: 'target/VinayDevOpsLab-0.0.1-SNAPSHOT.war', type: 'war']], credentialsId: 'Nexus-credential', groupId: "${ GroupId}", nexusUrl: '10.0.0.74:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'keita-snapshot', version: "${Version}"
            }
        }
        stage("Print environment information"){
            steps{
                echo "ArtifactId is '${ArtifactID}'"
                echo "version is '${Version}'"
                echo "Name is '${Name}'"
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

