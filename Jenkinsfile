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
                nexusArtifactUploader artifacts:
                 [[artifactId: '${POM_ARTIFACTID}',
                  classifier: '',
                   file: 'target/${POM_ARTIFACTID}-${POM_VERSION}.${POM_PACKAGING}',
                    type: '${POM_PACKAGING}']],
                     credentialsId: 'NexusID',
                      groupId: '${POM_GROUPID}',
                       nexusUrl: '54.87.55.10:8081',
                        nexusVersion: 'nexus3',
                         protocol: 'http',
                          repository: 'biom',
                           version: '${POM_VERSION}'
            }

        }
        stage('list the dir'){
            steps{
                sh 'ls'
            }

        }
    }
}