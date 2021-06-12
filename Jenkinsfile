pipeline {

  agent any 
  tools {
    maven 'maven'
    jdk 'JDK8'
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
  }  
  stages {
    stage("Build") {   
      steps {
        echo 'build application'  
        sh 'mvn -B -DskipTests clean package'    
      } 
      post {
        success {
          junit 'target/surefire-reports/**/*.xml' 
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
