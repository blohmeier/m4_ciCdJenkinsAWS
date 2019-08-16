pipeline {
  agent any
  stages {
    stage ('Lint HTML ') {
      steps {
        sh 'tidy -q -e --doctype strict *.html'
      }
    }       
    stage ('Upload to AWS ') { 
      steps {
        withAWS(credentials: 'aws-static') {
          s3Upload(file:'index.html', bucket:'uniquenameproj4new', path:'index.html')
        }
      }
    }
  }
}
