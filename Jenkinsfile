pipeline {

  agent any 
  tools {
    maven 'maven'
    jdk 'JDK'
  }
  stages{
    stage ('Initialize') {
      steps {
        sh '''
            echo "PATH = ${PATH}"
            echo "M2_HOME = ${M2_HOME}"
        '''
      }
    }   
    stage("Build") {   
      steps {
        echo 'build application'  
        sh 'mvn -B -DskipTests clean package'    
      }     
    }  
    stage("Sonarqube analysis") {
      steps {
        echo 'sonarqube analaysis' 
        withSonarQubeEnv('sonarqube'){
          sh "mvn sonar:sonar \
                -Dsonar.projectKey=sample" \
                -Dsonar.host.url=http://127.0.0.1:9000 
        }    
      }    
    }
    stage("test") {
      when {
        expression {
          BRANCH_NAME == 'master'
        }
      }
      steps {
        echo 'test application' 
        sh 'mvn test'     
      }    
    }
    stage("deploy") {
    
      steps {
        echo 'deploy application'      
      }
    
    }
  }


}
