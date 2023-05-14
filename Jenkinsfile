pipeline{
    triggers {
  pollSCM('* * * * *')
    }
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages{
        stage('build & SonarQube analysis'){
            agent any
            steps{
                withSonarQubeENV('sonar'){
                sh 'mvn sonar:sonar'
               }      
            }

        }
        
        stage('maven package') {
            steps {
               sh 'mvn clean'
               sh 'mvn install'
               sh 'mvn package'
        
    }
}  
stage('test') {
    step {
       sh 'mvn test'
        
stage('deploy')
  steps {
      echo 'deployment'
      }
        
    }
  }
}        
