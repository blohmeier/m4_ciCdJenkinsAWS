pipeline {
  agent any
  options {
          withAWS(credentials: 'aws-static')
  }
  stages {
    stage ('Upload to AWS ') { 
      steps {
        s3Upload(file:'index.html', bucket:'uniquenameproj4new', path:'~/home/ubuntu/static/index.html')
      }
    }
  }
}
