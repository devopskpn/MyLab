pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    environment{
        ArtifactId = readMavenPom().getArtifactId()
        Version = readMavenPom().getversion()
        GroupID = readMavenPom().getGroupId()
        Name = readMavenPom().getname()

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
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', 
                classifier: '', 
                file: 'target/VinayDevOpsLab-0.0.5-SNAPSHOT.war', 
                type: 'war']], 
                credentialsId: 'bfa7c4f4-3e4e-4311-8bef-481f1f85f9da', 
                groupId: 'com.vinaysdevopslab', 
                nexusUrl: '65.1.149.188:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'devopskpn-SNAPSHOT', 
                version: '0.0.5-SNAPSHOT'
            }
        }

        // Stage 4: Print some information
        stage ('Print Environment variables'){
            steps{
                echo "Artifact ID is '${ArtifactId}'"
                echo "Version is '${Version}'"
                echo "GroupID ID is '${GroupID}'"
                echo "Name ID is '${Name}'"

            }
        }

        // Stage5 : Deploying
        stage ('Deploy'){
            steps {
                echo ' Deploying......'

            }
        }
        
    }

}