pipeline {

  agent any 
  
  stages {
  
    stage("build") {
    
      steps {
        echo 'build application'  
        sh 'mvn -B -DskipTests clean package'    
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
        sh 'mvn test     
      }
    
    }
    stage("deploy") {
    
      steps {
        echo 'deploy application'      
      }
    
    }
  }
  post {
    always {
      
    }
    success {
    
    }
    failure {
    
    }
  }

}
