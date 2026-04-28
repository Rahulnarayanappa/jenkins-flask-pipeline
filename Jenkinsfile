pipeline {
  agent {label 'docker-agent' }
  stages { 
    stage ('Build') {
      agent { label 'docker-agent' }
      steps {
        echo "this is build stage"
      }
    }
    stage ('Deploy') {
      
      steps {
        echo "this is deploy stage"
      }
    }
    stage ('Test') {
      
      steps {
        echo "this is test stage"
      }
    }
  }
}
