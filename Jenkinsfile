pipeline {
    agent any
    stages {
        stage('Verify Branch') {
      steps {
        echo "$GIT_BRANCH"
      }
        }
        stage('Docker Build') {
          steps {
            pwsh(script: 'docker images -a')
            pwsh(script: """
              cd azure-vote/
              docker images -a
              docker build -t jenkins-pipeline .
              docker images -a
              cd ..
            """)
          }
        }
        stage('Echo on master') {
           when {branch 'master'}
           steps {
              echo 'This is master branch'
           }
        }
        stage('Echo on add-tests') {
           when {branch 'add-tests'}
           steps {
              echo 'This is add-tests branch'
           }
        }
    }
}
