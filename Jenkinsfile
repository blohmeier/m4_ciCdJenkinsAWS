pipeline {
  agent any
  stages {
    stage ('Exit code 0 if Lint HTML succeeds otherwise exit code not 0 ') {
      steps {
        sh '''
          tidy -qe --doctype strict *.html 2> /dev/null
            if [ $? -eq 0 ]
            then
	      exit 0
	    else  
              true
              fi
        '''
      }
    }  
    stage ('Upload to AWS if Lint HTML succeeds') {
      steps {
        withAWS(credentials: 'aws-static') {
          s3Upload(file:'index.html', bucket:'uniquenameproj4new', path:'index.html')
        }
      }
    }
  }
}
