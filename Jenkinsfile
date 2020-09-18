pipeline {
   agent any

   stages {
      stage("Checkout") {
         steps {
            echo "Checking out fab... on $NODE_NAME : with the following labels $NODE_LABELS"
         }
      }

      stage("Cloning") {
         steps {
            echo "Clone other dependent repos with fab.mod & setup.sh"
         }
      }

      stage("Build RELEASE") {
         steps {
            echo "Build release service services with fab build.clean build.all"
         }
      }

      stage("Testing") {
         steps {
            echo "Test RELEASE mode with fab test.all"
         }
      }

   }

   post {
      always {
         echo "Always interpret the test reports"
      }

      success {
         echo "Only performs this task on success"
      }

      failure {
         echo "Report why the pipe-line failed"
      }

   }

}
