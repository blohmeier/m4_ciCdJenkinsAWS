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
        def result = sh returnStatus: true, script: './build.sh'
        if (result != 0) {
          echo '[FAILURE] Failed to build'
          currentBuild.result = 'FAILURE'
          // this will terminate the job if result is non-zero
          // You don't even have to set the result to FAILURE by hand
          sh "exit ${result}"
        }  
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
