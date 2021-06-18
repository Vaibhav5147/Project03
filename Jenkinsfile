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
        withSonarQubeEnv('DevsecopsPractice03'){
          bat 'mvn sonar:sonar'
          bat 'cat target/sonar/report-task.txt'
        }
      }
    }
  }
}
