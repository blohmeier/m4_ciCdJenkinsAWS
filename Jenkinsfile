pipeline {
  agent any
  stages {
    stage ('Upload to AWS ') {
      steps {
        withAWS(credentials: 'aws-staticNew') {
          s3Upload(file:'index.html', bucket:'uniquenameproj4new', path:'index.html')
        }
      }
    }
  }
}
