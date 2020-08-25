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
                    retry(3){
                        withAWS(region:'us-east-2',credentials:'aws-static'){
                        s3Upload(file:'index.html', bucket:'ahmed-jenkins-pipline', path:'')
                    }                             
                }
            }
        }
     }
}
