pipeline {
  agent any

  stages {
    stage('Download script') {
      steps {
        git branch: 'main', url: 'https://github.com/Mumume88/jenkins.git'
      }
    }

    stage('Run script') {
  steps {
    sh 'mysql --user rfamro --host mysql-rfam-public.ebi.ac.uk --port 4497 --database Rfam < script.sql > query_results.txt'
    sh 'cat query_results.txt'
  }
}

    stage('Test results') {
      steps {
        // Add testing steps here
      }
    }

    stage('Deploy script') {
      steps {
        sh 'mysql --user rfamro --host mysql-rfam-public.ebi.ac.uk --port 4497 --database Rfam < script.sql'
      }
    }
  }

  triggers {
    pollSCM('* * * * *')
  }
}