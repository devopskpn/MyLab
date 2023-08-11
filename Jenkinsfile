pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
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
                echo ' Testing......'

            }
        }
        // Stage 3 : Publish the artefacts to Nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.5-SNAPSHOT.war', type: 'war']], credentialsId: 'bfa7c4f4-3e4e-4311-8bef-481f1f85f9da', groupId: 'com.vinaysdevopslab', nexusUrl: '65.1.149.188:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'devopskpn-SNAPSHOT', version: '0.0.5-SNAPSHOT'
            }
        }



        // Stage3 : Deploying
        stage ('Deploy'){
            steps {
                echo ' Deploying......'

            }
        }
        
    }

}