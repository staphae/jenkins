pipeline {
  agent any
  stages {
    stage('Clone-Fab') {
      steps {
        echo "Checking out fab... on $NODE_NAME : with the following labels $NODE_LABELS"
      }
    }

    stage('Exec-fab-mod-all') {
      steps {
        echo 'Clone other dependent repos with fab.mod & setup.sh'
      }
    }

    stage('Build(Release)') {
      parallel {
        stage('Build(Release)') {
          steps {
            echo 'Build release service services with fab build.clean build.all'
            echo 'Testing Release Build'
            echo 'Analyzing Release Build Results'
          }
        }

        stage('Build(Debug)') {
          steps {
            echo 'Build Debug Configuration'
            echo 'Testing Debug Build'
            echo 'Analyzing Debug Build Results'
          }
        }

      }
    }

  }
  post {
    always {
      echo 'Always interpret the test reports'
    }

    success {
      echo 'Only performs this task on success'
    }

    failure {
      echo 'Report why the pipe-line failed'
    }

  }
}