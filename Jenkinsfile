pipeline{
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages{
        stage('maven build'){
            steps{
                sh 'mvn clean install package'
            }

        }
        stage('upload artifact'){
            steps{
                script{
                    def mavenPom = readMavenPom file: 'pom.xml'
                    nexusArtifactUploader artifacts:
                    [[artifactId: "${mavenPOM.artifactId}",
                    classifier: '',
                    file: "target/${mavenPOM.artifactId}-${mavenPOM.version}.${mavenPOM.packaging}",
                    type: "${mavenPOM.packaging}"]],
                    credentialsId: 'NexusID',
                    groupId: "${mavenPOM.groupId}",
                     nexusUrl: '54.87.55.10:8081',
                      nexusVersion: 'nexus3',
                       protocol: 'http',
                        repository: 'biom',
                         version: "${mavenPOM.version}"
                  }          
            }

        }
        stage('list the dir'){
            steps{
                sh 'ls'
            }

        }
    }
}