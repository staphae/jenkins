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

    stage('Build(Debug)') {
      parallel {
        stage('Build(Debug)') {
          steps {
            echo 'Build Debug Configuration'
            echo 'Testing Debug Build'
            echo 'Analyzing Debug Build Results'
          }
        }

        stage('Build(Release)') {
          steps {
            echo 'Build Release Configuration'
            echo 'Test Release Build'
            echo 'Analyze Release Build Results'
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