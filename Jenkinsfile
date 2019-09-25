pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello World"'
        sh '''
          echo "Multiline shell steps works too"
          ls -lah
        '''
      }
    }
    stage('Lint HTML') {
         steps {
             sh 'tidy -q -e *.html'
         }
    }
    stage('Upload to AWS') {
      steps {
        withAWS(region:'eu-west-1',credentials:'307281617311') {
          s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-devops')
        }
      }
    }
  }
}
