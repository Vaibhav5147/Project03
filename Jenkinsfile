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
    stage ('Deploy-To-Tomcat')
    {
      steps 
      {
         bat "copy target\\JenkinsWar.war \"${C:/Program Files/Apache Software Foundation/Tomcat 9.0/webapps}\\JenkinsWar.war\""            
      }
    }
  }
}
