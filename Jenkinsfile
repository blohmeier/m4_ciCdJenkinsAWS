pipeline {
  agent any
  stages {
    stage ('Lint HTML ') {
      steps {
        sh 'tidy -qe --doctype strict *.html'
      }
    }       
    stage ('Quit if Lint HTML results in errors ') {
      steps { 
        sh 'if [[ $(ls -A) ]]; then'
        sh 'exit 1;'
        sh 'fi;'
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
