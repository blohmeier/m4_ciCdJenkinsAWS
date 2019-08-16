pipeline {
  agent any
  options {
          withAWS(credentials: 'aws-static')
  }
  stages {
    stage ('Lint HTML ') {
      steps {
        sh 'tidy -q -e *html'
      }
    }       
    stage ('Upload to AWS ') { 
      steps {
        s3Upload(file:'index.html', bucket:'uniquenameproj4new', path:'index.html')
      }
    }
  }
}
