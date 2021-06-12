pipeline {

  agent any 
  
  stages {
  
    stage("build") {
    
      steps {
        echo 'build application'  
        sh 'mvn2 -B -DskipTests clean package'    
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
