pipeline {
  agent any
  stages {
    stage ('Lint HTML ') {
      steps {
        sh 'tidy -qe -access 3 --doctype strict *.html'
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
