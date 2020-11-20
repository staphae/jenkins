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
      steps {
        echo 'Build release service services with fab build.clean build.all'
      }
    }

    stage('Testing(Release)') {
      steps {
        echo 'Test RELEASE mode with fab test.all'
      }
    }

    stage('Analyze(Release)') {
      steps {
        echo 'Analyzing results from release regression tests.'
      }
    }

    stage('Build(Debug)') {
      steps {
        echo 'Bulding DEUG build of tRoot H5'
      }
    }

    stage('Testing(Debug)') {
      steps {
        echo 'Executing test cases for DEBUG build'
      }
    }

    stage('Analyze(Debug)') {
      steps {
        echo 'Analyzing tesing cases for DEBUG build'
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