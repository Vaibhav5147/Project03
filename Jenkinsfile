pipeline {
  agent any
  tools 
  {
    jdk 'JAVA'
    maven 'Maven'
  }
  
  stages 
  {
    stage ('Initialize')
    {
      steps 
      {
        bat '''
                       echo "PATH = ${PATH}"
                       echo "M2_HOME = ${M2_HOME}"
           '''            
      }
    }
    stage ('Build')
    {
      steps
      {
        bat 'mvn clean package'
      }
    }
    stage('SAST')
    {
      steps
      {
        withSonarQubeEnv('Sonar'){
          bat 'mvn sonar:sonar'
          
        }
      }
    }
  }
}
