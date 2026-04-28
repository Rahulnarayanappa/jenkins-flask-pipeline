pipeline {
  agent {label 'slave-1' }
  stages { 
    stage ('Build') {
          steps {
            script { 
                sh 'docker build -t rahulnarayanappa/jenkins-flask:latest .'
              }
            }
          }
    stage ('Test') {      
        steps {
          sh 'pip install -r app/requirements.txt'
          sh 'pytest app/test_app.py'
      }
    }
    stage ('Push to Docker Hub') {
      steps {
        script { 
          docker.withRegistry('', 'docker-hub-creds') { 
                sh 'docker push rahulnarayanappa/jenkins-flask:latest'
          }
        }
      }
    }
    stage ('Deploy') {
     steps {
        sh 'docker stop flask-app || true && docker rm flask-app || true'
        sh 'docker run -d -p 5000:5000 --name flask-app rahulnarayanappa/jenkins-flask:latest'
      }
    }
  }
}
